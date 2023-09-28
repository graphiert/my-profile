<script>
	const profileImg = '/assets/galih.jpg';

	import { Card, Avatar } from 'flowbite-svelte';
</script>

<section class="flex justify-center content-around mt-8 mb-6 flex-wrap text-slate-900">
	<Card padding="xl" size="xl">
		<div class="p-6 px-20 flex flex-col items-center">
			<Avatar size="xl" src={profileImg} />
			<h5 class="mb-1 mt-2 mb text-xl font-medium text-gray-900 dark:text-white">Galih</h5>
			<span class="text-sm text-gray-500 dark:text-gray-400">Aku mah masih pemula</span>
		</div>
		<div class="flex justify-center text-xl gap-4">
			<a href="https://instagram.com/graphiert">
				<i class="bi bi-instagram"></i>
			</a>
			<a href="https://twitter.com/graphiert">
				<i class="bi bi-twitter"></i>
			</a>
			<a href="https://t.me/graphiert">
				<i class="bi bi-telegram"></i>
			</a>
		</div>
	</Card>
</section>

<section class="flex justify-center content-around mt-8 mb-6 flex-wrap text-slate-900">
	<div class="mt-8 md:w-2/3">
		<h3 class="mb-4 text-center text-3xl font-bold">About Me!</h3>

		<div class="my-5 text-md indent-8">
			<p>
				Hai semua! Kenalin, aku Galih. Ya, panggil aja aku Galih. Aku asli orang Grobogan, yang di
				Jawa Tengah itu loh. Ya saat ini aku lagi duduk di bangku SMA, bentar lagi bisa lah lulus
				hehehe.
			</p>
		</div>
		<div class="mb-5 text-md indent-8">
			<p>
				Kalo ditanya tentang hobi sih sebenernya bisa macem-macem. Bisa tergantung berdasarkan emang
				lagi tertarik sama sesuatu, kadang juga suka nulis-nulis gak jelas juga di blog ini (masih
				rencana, tapi semoga). Ada lah dikit-dikit suka cosplay tapi kan ya kadang bisa juga agak
				males, tergantung mood juga tergantung isi dompet hehe. Suka ngoding juga biar tau ada apa
				aja yang lagi rame lah, juga biar dianggap paling keren satu kelas. Walau emang ada
				pelajaran informatika di kelasku, tapi rata-rata temenku kalo susah ya konsultasinya ke aku,
				bukan ke guru. Kan kesannya malah aneh ya, cosplay guru juga mungkin? Wow siapa sangka
				wkwkwk.
			</p>
		</div>
		<div class="mb-5 text-md indent-8">
			<p>
				Oh iya, aku orangnya doyan ngegame juga, tapi cuma main 3 game aja sih. Biasanya main
				Genshin Impact, kalau lagi males biasanya larinya ke CODM. Aku masih pemula kok, serius😭.
				Soalnya aku baru main tahun kemarin, tapi gatau aja kok kayaknya cepet banget naik ranknya.
				Oh iya, aku nyebut 3 game tadi ya. Yang satunya itu Honkai: Star Rail tapi aku lagi
				males-malesnya main game itu, karena emang lagi masa-masanya Genshin Impact naik daun lagi.
				Gatau deh sama Hoyoverse, salah satu game hypenya turun yang lain naik, gitu aja terus
				siklusnya. Apa ini genjutsunya Hoyoverse biar game mereka gak sepi? Gak tentu juga sih, ini
				pendapat pribadiku sendiri.
			</p>
		</div>
		<div class="mb-5 text-md indent-8">
			<p>
				Ya gitu aja sih. Kalo nanya soal skill, sebenernya aku juga masih belajar, belum menguasai
				semuanya. Tapi lagi berusaha biar bisa semua yang aku ingin kok. Itu aja dulu deh perkenalan
				singkat tentang aku, makasih deh buat kalian yang mau baca sampe sini. Btw kalo kalian mau
				donate saweria, <a class="underline" href="https://saweria.co/graphiert"
					>linknya ada di sini yak.</a
				> Makasi guys🔥!
			</p>
		</div>
	</div>
</section>
