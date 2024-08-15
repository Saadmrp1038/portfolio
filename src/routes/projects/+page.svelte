<script>
  import { onMount } from 'svelte';
  import { fade, fly } from 'svelte/transition';
  import Icon from 'svelte-awesome';
  import { faCode, faCalendar } from '@fortawesome/free-solid-svg-icons';

  const projects = [
    {
      name: "E-Bookopolis",
      technologies: ["HTML", "CSS", "JS", "EJS", "NodeJS", "ExpressJS", "Oracle"],
      description: "An online bookstore where users can buy books, track their purchases, and share blog posts. Admins manage the book collection, while users can interact through book reviews and blog comments.",
      course: "CSE-216 (Database) Course Project",
      color: "bg-indigo-600"
    },
    {
      name: "BDeHR",
      technologies: ["Svelte", "TailwindCSS", "TypeScript", "Java Springboot", "MySQL"],
      description: "A healthcare platform facilitating effortless access to medical records, promoting efficient patient-doctor collaboration while ensuring data privacy and security.",
      event: "Therap Javafest 2023",
      color: "bg-sky-600"
    },
    {
      name: "ConnectEd",
      technologies: ["Sveltekit", "TailwindCSS", "TypeScript", "Postgres", "Drizzle", "Shadcn-svelte"],
      description: "An innovative online study platform offering session management, collaborative tools such as group chat, group video call, sharing study resources, finding study partners, blog posts and moderation control.",
      course: "CSE408 (Software Development) Course Project",
      color: "bg-emerald-600"
    },
    {
      name: "CoderHub",
      technologies: ["Sveltekit", "TailwindCSS", "TypeScript", "Postgres", "Supabase", "DaisyUI"],
      description: "A platform for developers with features such as project management (upload, compare, download), video call, collaborative coding, groups, skill based matching with projects and AI chat.",
      event: "Code Crafters Dev Sprint 2024",
      color: "bg-rose-600"
    },
    {
      name: "BebshaAI",
      technologies: ["React", "Spring Boot", "Python", "Flask", "OpenAI API", "OpenCV", "Material UI"],
      description: "An AI powered platform aimed at empowering SMEs (Small and Midsize Enterprises) to establish their online presence by providing them with a website where they can effortlessly add and sell their products.",
      event: "SUST Hackathon 2024",
      color: "bg-amber-600"
    },
    {
      name: "Voyager",
      technologies: ["Sveltekit", "TailwindCSS", "TypeScript", "Postgres", "Drizzle", "DaisyUI"],
      description: "An attraction discovery website to help find detailed information, including weather, amenities, and user reviews of locations. Users can contribute their own travel experiences and suggest new attractions for others to explore.",
      event: "IUT OpenAPI Hackathon 2024",
      color: "bg-violet-600"
    },
    {
      name: "ShopGenie",
      technologies: ["Sveltekit", "TailwindCSS", "TypeScript", "Postgres", "Drizzle", "OpenAI API", "Selenium", "Python", "Flask"],
      description: "An AI powered shopping platform with 21000 products scraped from various sites supporting multi-modal search.",
      event: "YOBO Hackhathon 2024",
      color: "bg-cyan-600"
    },
    {
      name: "Sohojogi",
      technologies: ["Flutter", "Dart", "Supabase", "FastAPI"],
      description: "A mobile-based application designed to educate and inspire rural men to become advocates for gender equality, featuring offline access, Bengali language support, and various modules for community engagement and information sharing.",
      event: "Gen-Dev AI Hackhathon 2024",
      color: "bg-teal-600"
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

<div class="container mx-auto px-6 py-12">
  <h1 class="text-4xl font-bold mb-12 text-center text-white font-poppins">
    My Projects
  </h1>
  
  <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
    {#each projects as project, i}
      <div 
        class="project-card relative overflow-hidden rounded-lg shadow-lg transition-all duration-300 hover:shadow-2xl hover:scale-105 bg-slate-800"
        data-project={project.name}
      >
        {#if visibleProjects.includes(project.name)}
          <div in:fly="{{ y: 50, duration: 500, delay: i * 100 }}" out:fade>
            <div class={`absolute top-0 left-0 w-full h-2 ${project.color}`}></div>
            <div class="p-6">
              <h2 class="text-2xl font-bold mb-2 text-white">{project.name}</h2>
              <p class="text-sm mb-4 text-slate-300">{project.description}</p>
              <div class="flex flex-wrap gap-2 mb-4">
                {#each project.technologies as tech}
                  <span class="px-2 py-1 bg-slate-700 rounded-full text-xs text-slate-300">{tech}</span>
                {/each}
              </div>
              {#if project.course || project.event}
                <div class="flex items-center text-slate-400 text-sm">
                  <Icon data={project.course ? faCode : faCalendar} scale={1} class="mr-2" />
                  <span>{project.course || `Made for ${project.event}`}</span>
                </div>
              {/if}
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
  }
  .font-poppins {
    font-family: 'Poppins', sans-serif;
  }
</style>