<script>
  import { Router, Route } from 'svelte-navigator';
  import 'bootstrap-icons/font/bootstrap-icons.css';
  import './app.css';

  import Sidenav from './lib/Sidenav.svelte';
  import Hero from './lib/Jumbotron.svelte';
  // import Counter from './lib/Counter.svelte';
  import Changelog from './lib/Changelog.svelte';
  import Portfolio from './lib/Portfolio.svelte';
  import AnimeSearcher from './lib/portfolio/anime-searcher.svelte';
  import Todolist from './lib/portfolio/todolist.svelte';
  import Contact from './lib/Contact.svelte';
  import Notfound from './lib/Notfound.svelte';
</script>

<Router>
  <Sidenav />
  <main class="relative px-8 pt-[72px]">
    <Route path="/" component={Hero} primary={false} />
    <!-- <Route path="/counter" component={Counter} primary={false} /> -->
    <Route path="/changelog" component={Changelog} primary={false} />
    <Route path="/portfolio" component={Portfolio} primary={false} />
    <Route path="/portfolio/anime-searcher" component={AnimeSearcher} primary={false} />
    <Route path="/portfolio/todolist" component={Todolist} primary={false} />
    <Route path="/contact" component={Contact} primary={false} />
    <Route path="*" component={Notfound} primary={false} />
  </main>
</Router>
