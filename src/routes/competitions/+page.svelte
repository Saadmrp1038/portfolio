<script>
  import { onMount } from 'svelte';
  import { fade, fly } from 'svelte/transition';
  import Icon from 'svelte-awesome';
  import { faTrophy, faMedal, faCertificate } from '@fortawesome/free-solid-svg-icons';

  const competitions = [
    {
      year: 2024,
      events: [
        {
          name: "IUT 11th National ICT Fest 2024",
          achievement: "1st Place in OpenAPI Hackathon",
          icon: faTrophy
        },
        {
          name: "Code Crafters Dev Sprint 2024",
          achievement: "1st Place",
          icon: faTrophy
        },
        {
          name: "SUST CSE Carnival 2024",
          achievement: "1st Place in the Hackathon",
          icon: faTrophy
        }
      ]
    },
    {
      year: 2023,
      events: [
        {
          name: "Cefalo ITverse 2023",
          achievement: "1st Place in the Project Showcasing category",
          icon: faTrophy
        }
      ]
    },
    {
      year: 2022,
      events: [
        {
          name: "2022 ICPC Asia Dhaka Regional Contest",
          achievement: "11th place in the Preliminaries (4th from BUET), 27th place in the Regionals",
          icon: faMedal
        },
        {
          name: "BUET Inter University Programming Contest 2022",
          achievement: "31st Place",
          icon: faCertificate
        },
        {
          name: "SEC Inter University Junior Programming Contest 2022",
          achievement: "7th Place",
          icon: faMedal
        },
        {
          name: "AUST IUPC 2022",
          achievement: "21st Place",
          icon: faCertificate
        }
      ]
    }
  ];

  let visibleYears = [];

  onMount(() => {
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          visibleYears = [...visibleYears, entry.target.dataset.year];
        }
      });
    }, { threshold: 0.1 });

    document.querySelectorAll('.year-section').forEach(section => {
      observer.observe(section);
    });
  });
</script>

<div class="container mx-auto px-4 sm:px-6 py-8 sm:py-12">
  <h1 class="text-3xl sm:text-4xl font-bold mb-8 sm:mb-12 text-center text-white font-poppins">
    Competition Timeline
  </h1>
  
  <div class="relative">
    {#each competitions as yearGroup, i}
      <div class="year-section mb-12 sm:mb-16" data-year={yearGroup.year}>
        {#if visibleYears.includes(yearGroup.year.toString())}
          <div in:fly="{{ x: -50, duration: 500, delay: i * 200 }}" out:fade>
            <div class="flex items-center mb-6 sm:mb-8">
              <div class="w-16 h-16 sm:w-24 sm:h-24 rounded-full bg-slate-700 flex items-center justify-center text-xl sm:text-3xl font-bold text-white">
                {yearGroup.year}
              </div>
              <div class="flex-grow h-1 bg-slate-700 ml-4"></div>
            </div>
            <div class="ml-8 sm:ml-32 space-y-6 sm:space-y-8">
              {#each yearGroup.events as event, j}
                <div in:fly="{{ y: 50, duration: 500, delay: (i * 200) + (j * 100) }}" out:fade
                     class="bg-slate-800 rounded-lg p-4 sm:p-6 shadow-lg hover:shadow-2xl transition-all duration-300">
                  <div class="flex items-center mb-3 sm:mb-4">
                    <Icon data={event.icon} scale={1.5} class="mr-3 sm:mr-4 text-yellow-400" />
                    <h2 class="text-lg sm:text-xl font-bold text-white">{event.name}</h2>
                  </div>
                  <p class="text-xs sm:text-sm text-slate-300">{event.achievement}</p>
                </div>
              {/each}
            </div>
          </div>
        {/if}
      </div>
    {/each}
    <div class="absolute top-0 bottom-0 left-8 sm:left-12 w-0.5 bg-slate-700"></div>
  </div>
</div>

<style>
  :global(body) {
    font-family: 'Inter', sans-serif;
  }
  .font-poppins {
    font-family: 'Poppins', sans-serif;
  }

  @media (max-width: 640px) {
    .year-section {
      padding-left: 1rem;
    }
  }
</style>