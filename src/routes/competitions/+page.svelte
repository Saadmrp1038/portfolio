<script>
	import { onMount } from 'svelte';
	import { fade, fly } from 'svelte/transition';
	import Icon from 'svelte-awesome';
	import {
		faTrophy,
		faMedal,
		faCertificate,
		faFileAlt,
		faAward,
		faExternalLinkAlt,
		faChevronDown,
		faChevronUp,
		faTimes
	} from '@fortawesome/free-solid-svg-icons';

	// Import all certificate images
	import austIUPC from '$lib/assets/AUST IUPC 2022_Participation Certificate.jpeg';
	import devSprint from '$lib/assets/Dev Sprint_Champion.jpg';
	import genDev from '$lib/assets/Gen-Dev.png';
	import icpcAsiaDhaka from '$lib/assets/ICPC Asia Dhaka Regional 2022_Participation Certificate.jpeg';
	import itVerse from '$lib/assets/ITVersre_TechTales_Champion.png';
	import iutNationalICT from '$lib/assets/IUT National ICT Fest_OpenAPI Hackhathon_Champion.jpeg';
	import secCSEFest from '$lib/assets/SEC CSE Fest 2022_7th.jpeg';
	import sustCSECarnival from '$lib/assets/SUST CSE Carnival_Hackhathon_Champion.jpg';
	import BCOLBC2024 from '$lib/assets/BCOLBD 2024.jpg'

	// Create a map of certificate names to their imported images
	const certificateMap = {
		'BCOLBD 2024.jpg': BCOLBC2024,
		'AUST IUPC 2022_Participation Certificate.jpeg': austIUPC,
		'Dev Sprint_Champion.jpg': devSprint,
		'Gen-Dev.png': genDev,
		'ICPC Asia Dhaka Regional 2022_Participation Certificate.jpeg': icpcAsiaDhaka,
		'ITVersre_TechTales_Champion.png': itVerse,
		'IUT National ICT Fest_OpenAPI Hackhathon_Champion.jpeg': iutNationalICT,
		'SEC CSE Fest 2022_7th.jpeg': secCSEFest,
		'SUST CSE Carnival_Hackhathon_Champion.jpg': sustCSECarnival
	};

	const competitions = [
		{
			year: 2024,
			events: [
				{
					name: 'BCOLBD 2024 AI Category',
					achievement: "Honorable Mention",
					icon: faMedal,
					certificate: 'BCOLBD 2024.jpg'
				},
				{
					name: 'Gen-Dev AI Hackathon: Gender Knowledge Augmentation',
					achievement: "Runner's-up",
					icon: faMedal,
					certificate: 'Gen-Dev.png'
				},
				{
					name: 'IUT 11th National ICT Fest 2024',
					achievement: '1st Place in OpenAPI Hackathon',
					icon: faTrophy,
					certificate: 'IUT National ICT Fest_OpenAPI Hackhathon_Champion.jpeg'
				},
				{
					name: 'Code Crafters Dev Sprint 2024',
					achievement: '1st Place',
					icon: faTrophy,
					certificate: 'Dev Sprint_Champion.jpg'
				},
				{
					name: 'SUST CSE Carnival 2024',
					achievement: '1st Place in the Hackathon',
					icon: faTrophy,
					certificate: 'SUST CSE Carnival_Hackhathon_Champion.jpg'
				}
			]
		},
		{
			year: 2023,
			events: [
				{
					name: 'Cefalo ITverse 2023',
					achievement: '1st Place in the Project Showcasing category',
					icon: faTrophy,
					certificate: 'ITVersre_TechTales_Champion.png'
				}
			]
		},
		{
			year: 2022,
			events: [
				{
					name: '2022 ICPC Asia Dhaka Regional Contest',
					achievement:
						'11th place in the Preliminaries (4th from BUET), 27th place in the Regionals',
					icon: faMedal,
					certificate: 'ICPC Asia Dhaka Regional 2022_Participation Certificate.jpeg'
				},
				{
					name: 'BUET Inter University Programming Contest 2022',
					achievement: '31st Place',
					icon: faCertificate
				},
				{
					name: 'SEC Inter University Junior Programming Contest 2022',
					achievement: '7th Place',
					icon: faMedal,
					certificate: 'SEC CSE Fest 2022_7th.jpeg'
				},
				{
					name: 'AUST IUPC 2022',
					achievement: '21st Place',
					icon: faCertificate,
					certificate: 'AUST IUPC 2022_Participation Certificate.jpeg'
				}
			]
		}
	];

	let visibleYears = [];
    let selectedCertificate = null;
    let isMobile = false;

    onMount(() => {
        const observer = new IntersectionObserver(
            (entries) => {
                entries.forEach((entry) => {
                    if (entry.isIntersecting) {
                        visibleYears = [...visibleYears, entry.target.dataset.year];
                    }
                });
            },
            { threshold: 0.1 }
        );

        document.querySelectorAll('.year-section').forEach((section) => {
            observer.observe(section);
        });

        // Check if device is mobile
        const checkMobile = () => {
            isMobile = window.innerWidth <= 768;
        };
        
        checkMobile();
        window.addEventListener('resize', checkMobile);

        return () => {
            window.removeEventListener('resize', checkMobile);
        };
    });

    function showCertificate(certificateName) {
        selectedCertificate = certificateName;
    }

    function closeCertificate() {
        selectedCertificate = null;
    }
</script>

<svelte:head>
	<title>Competitions - Saad Mohammad Rafid Pial</title>
</svelte:head>

<div class="container mx-auto px-2 sm:px-4 py-4 sm:py-8">
	<h1 class="text-4xl font-bold mb-12 text-center text-white font-poppins">
      Competition Timeline
  </h1>

  <div class="relative">
      {#each competitions as yearGroup, i}
          <div class="year-section mb-8 sm:mb-12" data-year={yearGroup.year}>
              {#if visibleYears.includes(yearGroup.year.toString())}
                  <div in:fly={{ x: -50, duration: 500, delay: i * 200 }} out:fade>
                      <div class="flex items-center mb-3 sm:mb-4 relative">
                          <div
                              class="w-12 h-12 sm:w-16 sm:h-16 md:w-20 md:h-20 rounded-full bg-gradient-to-br from-slate-600 to-slate-800 flex items-center justify-center text-base sm:text-lg md:text-xl font-bold text-white shadow-lg z-10"
                          >
                              {yearGroup.year}
                          </div>
                          <div class="flex-grow h-1 bg-slate-700 ml-3 sm:ml-4"></div>
                      </div>
                      <div class="ml-6 sm:ml-8 md:ml-10 space-y-3 sm:space-y-4 relative">
                          <div class="absolute top-[-18px] sm:top-[-24px] bottom-0 left-0 w-0.5 bg-slate-700"></div>
                          {#each yearGroup.events as event, j}
                              <div
                                  in:fly={{ y: 50, duration: 500, delay: i * 200 + j * 100 }}
                                  out:fade
                                  class="bg-slate-800 rounded-lg p-2 sm:p-4 md:p-6 shadow-lg hover:shadow-2xl transition-all duration-300 transform hover:-translate-y-1 ml-4 sm:ml-6 relative"
                              >
                                  <div class="flex flex-col md:flex-row md:items-start">
                                      <div class="flex-grow">
                                          <div class="flex items-center mb-2 md:mb-3">
                                              <Icon data={event.icon} scale={1.2} class="mr-2 md:mr-3 text-yellow-400" />
                                              <h2 class="text-base sm:text-lg md:text-xl font-bold text-white">{event.name}</h2>
                                          </div>
                                          <p class="text-sm text-slate-300 mb-2 sm:mb-3">{event.achievement}</p>
                                          {#if event.certificate}
                                              <button
                                                  class="bg-blue-500 hover:bg-blue-600 text-white px-3 py-1 rounded-full text-sm transition-colors duration-300"
                                                  on:click={() => showCertificate(event.certificate)}
                                              >
                                                  View Certificate
                                              </button>
                                          {/if}
                                      </div>
                                  </div>
                              </div>
                          {/each}
                      </div>
                  </div>
              {/if}
          </div>
      {/each}
  </div>
</div>
{#if selectedCertificate}
    <div class="fixed inset-0 bg-black bg-opacity-75 flex items-center justify-center p-4 z-50" in:fade out:fade>
        <div class="bg-white rounded-lg p-4 w-full max-w-3xl max-h-[90vh] overflow-auto">
            <div class="flex justify-between items-center mb-4">
                <h3 class="text-lg md:text-xl font-bold text-gray-800">Certificate Preview</h3>
                <button on:click={closeCertificate} class="text-gray-500 hover:text-gray-700">
                    <Icon data={faTimes} scale={1.5} />
                </button>
            </div>
            <img src={certificateMap[selectedCertificate]} alt="Certificate" class="w-full h-auto" />
        </div>
    </div>
{/if}

<style>
  :global(body) {
      font-family: 'Inter', sans-serif;
      background-color: #1e293b; /* This matches slate-800 */
      color: #e2e8f0;
  }
  .font-poppins {
      font-family: 'Poppins', sans-serif;
  }

  @media (max-width: 640px) {
      .year-section {
          padding-left: 0.5rem;
      }
  }
</style>