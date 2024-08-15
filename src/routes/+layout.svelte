<script>
  import "../app.css";
  import { faGithub, faLinkedin } from '@fortawesome/free-brands-svg-icons';
  import { faEnvelope, faBars } from '@fortawesome/free-solid-svg-icons';
  import Icon from 'svelte-awesome';
  import { page } from '$app/stores';
  import { fly } from 'svelte/transition';
  import profilePic from '$lib/assets/pial.jpg';
  import { base } from '$app/paths';

  let isMenuOpen = false;

  $: currentPath = $page.url.pathname;

  function toggleMenu() {
    isMenuOpen = !isMenuOpen;
  }
</script>

<svelte:head>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&family=Poppins:wght@700&display=swap" rel="stylesheet">
</svelte:head>

<div class="min-h-screen flex flex-col bg-slate-900 text-white font-inter">
  <header class="bg-slate-800 shadow-md">
    <div class="container mx-auto px-6 py-4">
      <nav class="flex justify-between items-center">
        <a href="{base}/" class="flex items-center space-x-3">
          <img src={profilePic} alt="Saad Pial" class="w-10 h-10 rounded-full border-2 border-purple-500" />
          <span class="text-2xl font-bold bg-clip-text text-slate-400 font-poppins tracking-wide drop-shadow-md">
            Pial
          </span>
        </a>
        <div class="hidden md:flex space-x-6">
          {#each [
            { href: `${base}/`, label: 'Home' },
            { href: `${base}/about`, label: 'About' },
            { href: `${base}/projects`, label: 'Projects' },
            { href: `${base}/competitions`, label: 'Competitions' },
            { href: `${base}/skills`, label: 'Skills' },
            { href: `${base}/education`, label: 'Education' }
          ] as link}
            <a 
              href={link.href} 
              class="text-slate-300 hover:text-white transition duration-300 border-b-2 {currentPath === link.href ? 'border-purple-500' : 'border-transparent'}"
            >
              {link.label}
            </a>
          {/each}
        </div>
        <button class="md:hidden text-white" on:click={toggleMenu}>
          <Icon data={faBars} scale={1.5} />
        </button>
      </nav>
    </div>
  </header>

  {#if isMenuOpen}
    <div 
      class="md:hidden bg-slate-800 py-4"
      transition:fly={{ y: -100, duration: 300 }}
    >
      {#each [
         { href: `${base}/`, label: 'Home' },
            { href: `${base}/about`, label: 'About' },
            { href: `${base}/projects`, label: 'Projects' },
            { href: `${base}/competitions`, label: 'Competitions' },
            { href: `${base}/skills`, label: 'Skills' },
            { href: `${base}/education`, label: 'Education' }
      ] as link}
        <a 
          href={link.href} 
          class="block py-2 px-6 text-slate-300 hover:bg-slate-700 transition duration-300 {currentPath === link.href ? 'bg-slate-700' : ''}"
          on:click={() => isMenuOpen = false}
        >
          {link.label}
        </a>
      {/each}
    </div>
  {/if}

  <main class="flex-grow container mx-auto px-6 py-8">
    <slot />
  </main>

  <footer class="bg-slate-800 shadow-inner">
    <div class="container mx-auto px-6 py-8">
      <div class="flex flex-col md:flex-row justify-between items-center">
        <div class="mb-4 md:mb-0 text-center md:text-left">
          <h3 class="text-xl font-semibold font-poppins">Saad Mohammad Rafid Pial</h3>
          <p class="text-slate-400">Competitive Programmer | AI Enthusiast | Full Stack Developer</p>
        </div>
        <div class="flex space-x-6">
          <a href="mailto:saadmrp222@gmail.com" class="text-slate-400 hover:text-white transition duration-300 transform hover:scale-110">
            <Icon data={faEnvelope} scale={1.5} />
          </a>
          <a href="https://github.com/Saadmrp1038" target="_blank" rel="noopener noreferrer" class="text-slate-400 hover:text-white transition duration-300 transform hover:scale-110">
            <Icon data={faGithub} scale={1.5} />
          </a>
          <a href="https://www.linkedin.com/in/saadmrp" target="_blank" rel="noopener noreferrer" class="text-slate-400 hover:text-white transition duration-300 transform hover:scale-110">
            <Icon data={faLinkedin} scale={1.5} />
          </a>
        </div>
      </div>
      <div class="mt-8 text-center text-slate-400 text-sm">
        © {new Date().getFullYear()} Saad Mohammad Rafid Pial. All rights reserved.
      </div>
    </div>
  </footer>
</div>

<style>
  :global(body) {
    font-family: 'Inter', sans-serif;
  }
  .font-poppins {
    font-family: 'Poppins', sans-serif;
  }
</style>