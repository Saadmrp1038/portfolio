<script>
  import { onMount } from 'svelte';
  import { fade, fly } from 'svelte/transition';
  import { faTrophy, faCode, faGraduationCap, faLaptopCode, faRobot, faPuzzlePiece } from '@fortawesome/free-solid-svg-icons';
  import Icon from 'svelte-awesome';

  let typedText = '';
  let fullText = "Saad Mohammad Rafid Pial";
  let cursorVisible = true;
  let showContent = false;

  onMount(() => {
    typeText();
    setInterval(() => {
      cursorVisible = !cursorVisible;
    }, 500);
  });

  function typeText() {
    let i = 0;
    const interval = setInterval(() => {
      if (i < fullText.length) {
        typedText += fullText[i];
        i++;
      } else {
        clearInterval(interval);
        setTimeout(() => {
          showContent = true;
        }, 500);
      }
    }, 100);
  }

  const skills = [
    { icon: faLaptopCode, name: "Competitive Programming" },
    { icon: faRobot, name: "Artificial Intelligence" },
    { icon: faPuzzlePiece, name: "Problem Solving" },
    { icon: faCode, name: "Full Stack Development" },
  ];

  const achievements = [
    { icon: faTrophy, title: "Hackathon Champion", description: "1st place in multiple competitions" },
    { icon: faCode, title: "Codeforces Candidate Master", description: "Achieved CM ranking (1900+)" },
    { icon: faGraduationCap, title: "BUET Undergrad", description: "4th year CSE student" },
  ];
</script>

<svelte:head>
  <title>Saad Mohammad Rafid Pial - Competitive Programmer & AI Enthusiast</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&family=Poppins:wght@700&display=swap" rel="stylesheet">
</svelte:head>

<div class="min-h-screen bg-gradient-to-br from-gray-900 via-gray-800 to-gray-900 text-white py-12 px-4 sm:px-6 lg:px-8 font-inter">
  <div class="max-w-7xl mx-auto">
    <div class="text-center mb-16">
      <h1 class="text-5xl sm:text-6xl font-bold mb-4 font-poppins">
        <span class="text-transparent bg-clip-text bg-gradient-to-r from-cyan-400 to-purple-500">
          {typedText}
        </span>
        <span class={cursorVisible ? 'opacity-100' : 'opacity-0'}>|</span>
      </h1>
      {#if showContent}
        <p in:fade class="text-xl text-gray-300 mt-4">Competitive Programmer | AI Enthusiast | Full Stack Developer</p>
      {/if}
    </div>

    {#if showContent}
      <div in:fade={{ delay: 300 }} class="mb-20">
        <h2 class="text-3xl font-bold mb-10 text-center font-poppins">My Arsenal</h2>
        <div class="grid grid-cols-2 md:grid-cols-4 gap-8">
          {#each skills as skill, i}
            <div in:fly={{ y: 50, delay: i * 100 }} class="flex flex-col items-center p-6 bg-gray-800 rounded-2xl shadow-lg hover:bg-gray-700 transition-all duration-300 transform hover:-translate-y-1">
              <Icon data={skill.icon} scale={2.5} class="mb-4 text-cyan-400" />
              <span class="text-center font-semibold">{skill.name}</span>
            </div>
          {/each}
        </div>
      </div>

      <div in:fade={{ delay: 600 }} class="mb-20">
        <h2 class="text-3xl font-bold mb-10 text-center font-poppins">Achievements</h2>
        <div class="grid md:grid-cols-3 gap-8">
          {#each achievements as achievement, i}
            <div in:fly={{ x: i % 2 === 0 ? -50 : 50, delay: i * 100 }} class="flex flex-col items-center p-6 bg-gradient-to-br from-gray-800 to-gray-700 rounded-2xl shadow-lg hover:shadow-xl transition-all duration-300 transform hover:-translate-y-1">
              <Icon data={achievement.icon} scale={2.5} class="mb-4 text-purple-400" />
              <h3 class="text-xl font-semibold mb-2">{achievement.title}</h3>
              <p class="text-gray-300 text-center">{achievement.description}</p>
            </div>
          {/each}
        </div>
      </div>

      <div in:fade={{ delay: 900 }} class="text-center">
        <h2 class="text-3xl font-bold mb-8 font-poppins">Ready to dive deeper?</h2>
        <div class="space-x-4">
          <a href="/projects" class="inline-block bg-gradient-to-r from-cyan-500 to-blue-500 text-white px-8 py-3 rounded-full font-semibold hover:from-cyan-600 hover:to-blue-600 transition duration-300 shadow-lg">Explore Projects</a>
          <a href="/competitions" class="inline-block bg-gradient-to-r from-purple-500 to-pink-500 text-white px-8 py-3 rounded-full font-semibold hover:from-purple-600 hover:to-pink-600 transition duration-300 shadow-lg">View Competitions</a>
        </div>
      </div>
    {/if}
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