<script>
  import { onMount } from 'svelte';
  import { fade, fly } from 'svelte/transition';
  import Icon from 'svelte-awesome';
  import { faGraduationCap, faCalendarAlt, faMapMarkerAlt, faStar } from '@fortawesome/free-solid-svg-icons';

  const educationData = [
    {
      degree: "B.Sc. in Computer Science and Engineering",
      institution: "Bangladesh University of Engineering and Technology (BUET)",
      duration: "2020 - Present",
      location: "Dhaka, Bangladesh",
      gpa: "CGPA: 3.37 (out of 4.00)",
      details: [
        "Currently in the fourth year of study",
        "Participated in numerous programming contests and hackathons",
        "Achieved Candidate Master ranking on Codeforces",
        "Qualified for 2022 ICPC Asia Dhaka Regional Contest"
      ]
    },
    {
      degree: "Higher Secondary Certificate (HSC)",
      institution: "Notre Dame College",
      duration: "2017 - 2019",
      location: "Dhaka, Bangladesh",
      gpa: "GPA: 5.00 (out of 5.00)",
      details: [
        "Achieved excellent academic results",
        "Developed strong foundation in science and mathematics"
      ]
    },
    {
      degree: "Secondary School Certificate (SSC)",
      institution: "Monipur High School & College",
      duration: "2015 - 2017",
      location: "Dhaka, Bangladesh",
      gpa: "GPA: 5.00 (out of 5.00)",
      details: [
        "Completed secondary education with outstanding performance",
        "Developed early interest in mathematics & problem solving",
        "Participated in school-level math & physics olympiads"
      ]
    }
  ];

  let visibleEducation = [];

  onMount(() => {
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          visibleEducation = [...visibleEducation, entry.target.dataset.education];
        }
      });
    }, { threshold: 0.1 });

    document.querySelectorAll('.education-item').forEach(item => {
      observer.observe(item);
    });
  });
</script>

<div class="container mx-auto px-4 sm:px-6 py-8 sm:py-12 bg-gray-900">
  <h1 class="text-3xl sm:text-4xl font-bold mb-8 sm:mb-12 text-center text-white font-poppins">
    My Educational Journey
  </h1>
  
  <div class="space-y-8 sm:space-y-12">
    {#each educationData as edu, i}
      <div class="education-item" data-education={edu.degree}>
        {#if visibleEducation.includes(edu.degree)}
          <div 
            in:fly="{{ y: 50, duration: 500, delay: i * 200 }}" 
            out:fade
            class="bg-slate-800 rounded-lg p-4 sm:p-6 shadow-lg hover:shadow-2xl transition-all duration-300 border-l-4 border-indigo-500"
          >
            <div class="flex items-center mb-3 sm:mb-4">
              <Icon data={faGraduationCap} scale={1.5} class="mr-3 sm:mr-4 text-indigo-400" />
              <h2 class="text-xl sm:text-2xl font-bold text-white">{edu.degree}</h2>
            </div>
            <div class="ml-8 sm:ml-12 space-y-2">
              <p class="text-lg sm:text-xl text-slate-300">{edu.institution}</p>
              <p class="text-xs sm:text-sm text-slate-400 flex items-center">
                <Icon data={faCalendarAlt} scale={0.8} class="mr-2" /> {edu.duration}
              </p>
              <p class="text-xs sm:text-sm text-slate-400 flex items-center">
                <Icon data={faMapMarkerAlt} scale={0.8} class="mr-2" /> {edu.location}
              </p>
              <p class="text-xs sm:text-sm text-indigo-400 flex items-center font-semibold">
                <Icon data={faStar} scale={0.8} class="mr-2" /> {edu.gpa}
              </p>
              <ul class="list-disc list-inside text-sm sm:text-base text-slate-300 mt-3 sm:mt-4">
                {#each edu.details as detail}
                  <li>{detail}</li>
                {/each}
              </ul>
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
    background-color: #1a202c;
  }
  .font-poppins {
    font-family: 'Poppins', sans-serif;
  }

  @media (max-width: 640px) {
    .education-item {
      padding-left: 0.5rem;
      padding-right: 0.5rem;
    }
  }
</style>