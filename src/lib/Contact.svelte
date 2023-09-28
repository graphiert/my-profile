<script>
	import { Input, Label, Textarea, Button, Alert } from 'flowbite-svelte';
	const dataForm = {
		nama: '',
		email: '',
		pesan: ''
	};

	let success = 0;
	// -1 = Gagal
	// 0 = Netral (belum disubmit)
	// 1 = Berhasil
	// 2 = Memproses

	const handleSubmit = async (e) => {
		success = 2;
		try {
			const req = await fetch(
				`https://api.telegram.org/bot${atob(
					'NTE1NDgxNzI4ODpBQUVFUld5STNERU1YQ2syU2JDd1ZKNGpwUnJNSjZvSTVDOA=='
				)}/sendMessage`,
				{
					body: JSON.stringify({
						chat_id: 1708159796,
						parse_mode: 'HTML',
						text: `<b>ADA PESAN BARU!</b>\n\n<b>Pengirim:</b> ${dataForm.nama}\n<b>Email:</b> ${dataForm.email}\n\n"${dataForm.pesan}"`
					}),
					method: 'POST',
					headers: {
						'content-type': 'application/json'
					}
				}
			);
			const res = await req.json();
			success = res.ok ? 1 : -1;
		} catch {
			success = -1;
		}

		if (success == 1) e.target.reset();
		setTimeout(() => {
			success = 0;
		}, 7000);
	};
</script>

<h2 class="text-2xl my-2 font-bold">Form Contact</h2>

<form class="my-6" on:submit|preventDefault={(e) => handleSubmit(e)}>
	{#if success != 0}
		<Alert color={success == 1 ? 'green' : success == -1 ? 'red' : 'blue'}>
			{#if success != 2}
				<span class="font-bold">{success == 1 ? 'Berhasil' : success == -1 ? 'Gagal' : ''}</span> mengirimkan
				pesan.
			{:else}
				Sedang mencoba untuk mengirimkan pesan...
			{/if}
		</Alert>
	{/if}
	<div class="my-6">
		<Label for="first_name" class="mb-2">Nama</Label>
		<Input type="text" id="first_name" placeholder="Nama" required bind:value={dataForm.nama} />
	</div>
	<div class="my-6">
		<Label for="email" class="mb-2">Alamat Email</Label>
		<Input
			type="email"
			id="email"
			placeholder="Alamat Email"
			required
			bind:value={dataForm.email}
		/>
	</div>
	<div class="my-6">
		<Label for="textarea-id" class="mb-2">Pesan</Label>
		<Textarea id="textarea-id" placeholder="Pesan" rows="4" required bind:value={dataForm.pesan} />
	</div>
	<Button color="blue" type="submit"><i class="bi bi-send mr-2"></i>Kirim</Button>
</form>
