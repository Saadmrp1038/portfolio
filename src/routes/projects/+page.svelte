<script>
  import { onMount } from 'svelte';
  import { fade, fly } from 'svelte/transition';
  import Icon from 'svelte-awesome';
  import { faCode, faCalendar, faExternalLinkAlt } from '@fortawesome/free-solid-svg-icons';

  // Import project logos
  import ebookopolis from '$lib/logos/ebookopolis.png';
  import bdehr from '$lib/logos/bdehr.png';
  import connected from '$lib/logos/connected.png';
  import coderhub from '$lib/logos/coderhub.png';
  import bebshaAI from '$lib/logos/bebshaAI.png';
  import voyager from '$lib/logos/voyager.png';
  import shopgenie from '$lib/logos/shopgenie.png';
  import sohojogi from '$lib/logos/sohojogi.png';

  const projects = [
    {
      name: "ShopGenie",
      technologies: ["Sveltekit", "TailwindCSS", "TypeScript", "Postgres", "Drizzle", "OpenAI API", "Selenium", "Python", "Flask"],
      description: "An AI powered shopping platform with 21000 products scraped from various sites supporting multi-modal search.",
      event: "YOBO Hackhathon 2024",
      logo: shopgenie,
      link: "https://github.com/yoboBUETGenesis"
    },
    {
      name: "BDeHR",
      technologies: ["Svelte", "TailwindCSS", "TypeScript", "Java Springboot", "MySQL"],
      description: "A healthcare platform facilitating effortless access to medical records, promoting efficient patient-doctor collaboration while ensuring data privacy and security.",
      event: "Therap Javafest 2023",
      logo: bdehr,
      link: "https://github.com/BDEHR-TherapJavaFest2023"
    },
    {
      name: "CoderHub",
      technologies: ["Sveltekit", "TailwindCSS", "TypeScript", "Postgres", "Supabase", "DaisyUI"],
      description: "A platform for developers with features such as project management (upload, compare, download), video call, collaborative coding, groups, skill based matching with projects and AI chat.",
      event: "Code Crafters Dev Sprint 2024",
      logo: coderhub,
      link: "https://github.com/Saadmrp1038/CoderHub"
    },
    {
      name: "BebshaAI",
      technologies: ["React", "Spring Boot", "Python", "Flask", "OpenAI API", "OpenCV", "Material UI"],
      description: "An AI powered platform aimed at empowering SMEs (Small and Midsize Enterprises) to establish their online presence by providing them with a website where they can effortlessly add and sell their products.",
      event: "SUST Hackathon 2024",
      logo: bebshaAI,
      link: "https://github.com/Saadmrp1038/BebshaAI-backend"
    },
    {
      name: "Voyager",
      technologies: ["Sveltekit", "TailwindCSS", "TypeScript", "Postgres", "Drizzle", "DaisyUI"],
      description: "An attraction discovery website to help find detailed information, including weather, amenities, and user reviews of locations. Users can contribute their own travel experiences and suggest new attractions for others to explore.",
      event: "IUT OpenAPI Hackathon 2024",
      logo: voyager,
      link: "https://github.com/Saadmrp1038/Voyager"
    },
    {
      name: "Sohojogi",
      technologies: ["Flutter", "Dart", "Supabase", "FastAPI"],
      description: "A mobile-based application designed to educate and inspire rural men to become advocates for gender equality, featuring offline access, Bengali language support, and various modules for community engagement and information sharing.",
      event: "Gen-Dev AI Hackhathon 2024",
      logo: sohojogi,
      link: "https://github.com/Saadmrp1038/Sohojogi_Mobile_App"
    },
    {
      name: "ConnectEd",
      technologies: ["Sveltekit", "TailwindCSS", "TypeScript", "Postgres", "Drizzle", "Shadcn-svelte"],
      description: "An innovative online study platform offering session management, collaborative tools such as group chat, group video call, sharing study resources, finding study partners, blog posts and moderation control.",
      course: "CSE408 (Software Development) Course Project",
      logo: connected,
      link: "https://github.com/Saadmrp1038/ConnectEd"
    },
    {
      name: "E-Bookopolis",
      technologies: ["HTML", "CSS", "JS", "EJS", "NodeJS", "ExpressJS", "Oracle"],
      description: "An online bookstore where users can buy books, track their purchases, and share blog posts. Admins manage the book collection, while users can interact through book reviews and blog comments.",
      course: "CSE-216 (Database) Course Project",
      logo: ebookopolis,
      link: "https://github.com/Saadmrp1038/E-Bookopolis"
    },
  ];

  let visibleProjects = [];

  onMount(() => {
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          visibleProjects = [...visibleProjects, entry.target.dataset.project];
        }
      });
    }, { threshold: 0.1 });

    document.querySelectorAll('.project-card').forEach(card => {
      observer.observe(card);
    });
  });
</script>

<svelte:head>
	<title>Projects - Saad Mohammad Rafid Pial</title>
</svelte:head>

<div class="container mx-auto px-2 sm:px-4 py-4 sm:py-8">
  <h1 class="text-4xl font-bold mb-12 text-center text-white font-poppins">
    My Projects
  </h1>
  
  <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
    {#each projects as project, i}
      <div 
        class="project-card relative overflow-hidden rounded-lg shadow-lg transition-all duration-300 hover:shadow-2xl hover:scale-105 bg-slate-800/50 backdrop-blur-sm border border-slate-700"
        data-project={project.name}
      >
        {#if visibleProjects.includes(project.name)}
          <div in:fly="{{ y: 50, duration: 500, delay: i * 100 }}" out:fade class="h-full flex flex-col">
            <div class="absolute top-0 left-0 w-full h-full opacity-5 filter blur-sm" style="background-image: url({project.logo}); background-size: cover; background-position: center;"></div>
            <div class="relative z-10 p-6 flex-grow flex flex-col">
              <div class="flex items-center mb-4">
                <img src={project.logo} alt={project.name} class="w-12 h-12 object-contain mr-4" />
                <h2 class="text-2xl font-bold text-white">{project.name}</h2>
              </div>
              <p class="text-sm mb-4 text-slate-300 flex-grow">{project.description}</p>
              <div class="flex flex-wrap gap-2 mb-4">
                {#each project.technologies as tech}
                  <span class="px-2 py-1 bg-slate-700/50 backdrop-blur-sm rounded-full text-xs text-slate-300">{tech}</span>
                {/each}
              </div>
              {#if project.course || project.event}
                <div class="flex items-center text-slate-400 text-sm mb-4">
                  <Icon data={project.course ? faCode : faCalendar} scale={1} class="mr-2" />
                  <span>{project.course || `Made for ${project.event}`}</span>
                </div>
              {/if}
              <a href={project.link} target="_blank" rel="noopener noreferrer" class="w-full py-2 px-4 bg-slate-700/50 backdrop-blur-sm text-white rounded hover:bg-slate-600/50 transition-colors duration-300 flex items-center justify-center">
                <Icon data={faExternalLinkAlt} scale={1} class="mr-2" />
                View on GitHub
              </a>
            </div>
          </div>
        {/if}
      </div>
    {/each}
  </div>
</div>

<style>
  :global(body) {
    font-family: 'Inter', sans-serif;
    background-color: #0f172a; /* Tailwind's slate-900 */
  }
  .font-poppins {
    font-family: 'Poppins', sans-serif;
  }
</style>