<script>
	import { onMount } from 'svelte';
	import { fade, fly } from 'svelte/transition';

	import {
		faCode,
		faLightbulb,
		faRocket,
		faBrain,
		faEnvelope,
		faPhone,
		faMapMarker
	} from '@fortawesome/free-solid-svg-icons';
	import { faGithub, faLinkedin } from '@fortawesome/free-brands-svg-icons';
	import Icon from 'svelte-awesome';
	import profilePic from '$lib/assets/pial.jpg';

	let showContent = false;

	onMount(() => {
		// Set a minimum delay to ensure the placeholder is visible
		setTimeout(() => {
			showContent = true;
		}, 300);
	});

	const highlights = [
		{
			icon: faCode,
			title: 'Competitive Programming',
			description: 'Candidate Master on Codeforces'
		},
		{ icon: faLightbulb, title: 'Innovation', description: 'Passion for AI and new technologies' },
		{ icon: faRocket, title: 'Hackathons', description: 'Multiple top positions secured' },
		{ icon: faBrain, title: 'Problem Solving', description: 'Critical thinker and quick learner' }
	];
</script>

<svelte:head>
	<title>About Me - Saad Mohammad Rafid Pial</title>
</svelte:head>

<div class="max-w-4xl mx-auto px-2 py-6 sm:py-12">
	<!-- Content Box with smooth transition -->
	<div
		class="content-box {showContent ? 'show' : ''} mb-8 sm:mb-12 bg-gradient-to-br from-gray-900 to-slate-800 p-4 sm:p-8 rounded-lg shadow-2xl"
	>
		<div
			in:fly={{ y: 20, duration: 600, delay: 200 }}
			class="flex flex-col sm:flex-row items-center mb-6 sm:mb-8"
		>
			<img
				src={profilePic}
				alt="Saad Mohammad Rafid Pial"
				class="rounded-full w-32 h-32 sm:w-48 sm:h-48 mb-4 sm:mb-0 sm:mr-8 border-4 border-purple-500 shadow-lg transform hover:scale-105 transition-transform duration-300"
			/>
			<div class="text-center sm:text-left">
				<h1
					class="text-3xl sm:text-4xl font-bold text-transparent bg-clip-text bg-gradient-to-r from-cyan-400 to-purple-500 font-poppins mb-2"
				>
					Saad Mohammad Rafid Pial
				</h1>
				<p class="text-lg sm:text-xl text-gray-300">
					Aspiring Software Engineer | AI Enthusiast | Competitive Programmer | Flutter Developer
				</p>
			</div>
		</div>

		<div class="space-y-4 sm:space-y-6 text-gray-300 leading-relaxed sm:text-base text-sm">
			<p in:fly={{ y: 20, duration: 600, delay: 400 }}>
				As a fourth-year undergraduate student majoring in CSE at BUET, I am driven by a deep love
				for technology and innovation. My journey in the field of computer science has been marked
				by a strong inclination towards competitive programming, critical thinking, and
				problem-solving.
			</p>

			<p in:fly={{ y: 20, duration: 500, delay: 600 }}>
				I have achieved the rank of <span class="text-cyan-400 font-semibold">Candidate Master on Codeforces</span>, showcasing my prowess in competitive programming. My participation in various hackathons has been equally rewarding, where I have secured top positions. These experiences have honed my skills in collaboration, quick thinking, and creative problem-solving under pressure.
			</p>

			<p in:fly={{ y: 20, duration: 500, delay: 800 }}>
				My interest in generative AI has led me to dive into several exciting projects, where I've tinkered with a variety of cool technologies. I've worked with languages like <span class="text-purple-400 font-semibold">Sveltekit, TailwindCSS, TypeScript, Flutter, Java, C/C++, Python</span>, and more. These projects have been a fun way to explore the world of AI and web development, pushing me to learn new skills and get creative with solutions.
			</p>

			<p in:fly={{ y: 20, duration: 500, delay: 1000 }}>
				Besides my technical skills, I'm all about keeping up with the latest tech and programming news. I thrive when I'm faced with new challenges that push me to grow. As graduation approaches, I am eager to contribute to an organization that values innovation, teamwork, and excellence.
			</p>

			<!-- Contact Information -->
			<div in:fly={{ y: 20, duration: 600, delay: 1200 }} class="bg-gray-800 bg-opacity-50 p-4 sm:p-6 rounded-lg shadow-lg mt-6 sm:mt-8">
				<h2 class="text-xl sm:text-2xl font-semibold mb-3 sm:mb-4 text-white">Contact Information</h2>
				<ul class="space-y-2 sm:space-y-3">
					<li class="flex items-center">
						<Icon data={faEnvelope} scale={1.2} class="text-cyan-400 mr-4" />
						<a href="mailto:saadmrp222@gmail.com" class="text-blue-400 hover:underline">saadmrp222@gmail.com</a>
					</li>
					<li class="flex items-center">
						<Icon data={faGithub} scale={1.2} class="text-gray-400 mr-4" />
						<a href="https://github.com/Saadmrp1038" target="_blank" rel="noopener noreferrer" class="text-blue-400 hover:underline">Saadmrp1038</a>
					</li>
					<li class="flex items-center">
						<Icon data={faLinkedin} scale={1.2} class="text-blue-400 mr-4" />
						<a href="https://www.linkedin.com/in/saadmrp" target="_blank" rel="noopener noreferrer" class="text-blue-400 hover:underline">saadmrp</a>
					</li>
					<li class="flex items-center">
						<Icon data={faPhone} scale={1.2} class="text-green-400 mr-4" />
						<span class="text-gray-300">01531551419</span>
					</li>
					<li class="flex items-center">
						<Icon data={faMapMarker} scale={1.2} class="text-red-400 mr-4" />
						<span class="text-gray-300">Dhaka, Bangladesh</span>
					</li>
				</ul>
			</div>
		</div>
	</div>

	<div in:fade={{ duration: 800, delay: 1400 }} class="grid grid-cols-1 sm:grid-cols-2 gap-4 sm:gap-6 mb-8 sm:mb-12">
		{#each highlights as highlight, i}
			<div
				in:fly={{ y: 20, duration: 600, delay: 1600 + i * 100 }}
				class="bg-gray-800 bg-opacity-50 p-4 sm:p-6 rounded-lg shadow-lg hover:shadow-xl transition-all duration-300 transform hover:-translate-y-1"
			>
				<Icon data={highlight.icon} scale={1.5} class="mb-3 sm:mb-4 text-purple-400" />
				<h3 class="text-lg sm:text-xl font-semibold mb-2 text-white">{highlight.title}</h3>
				<p class="text-sm sm:text-base text-gray-300">{highlight.description}</p>
			</div>
		{/each}
	</div>

	<div in:fade={{ duration: 800, delay: 2000 }} class="text-center">
		<a
			href="https://codeforces.com/profile/Reckless_Raccoon"
			target="_blank"
			rel="noopener noreferrer"
			class="inline-block bg-gradient-to-r from-cyan-500 to-blue-500 text-white px-6 sm:px-8 py-2 sm:py-3 rounded-full font-semibold text-sm sm:text-base hover:from-cyan-600 hover:to-blue-600 transition duration-300 shadow-lg transform hover:scale-105"
		>
			View My Codeforces Profile
		</a>
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

	/* Smooth transition for the content box */
	.content-box {
		opacity: 0;
		transform: scale(0.95);
		transition: opacity 0.5s ease, transform 0.5s ease;
	}

	.content-box.show {
		opacity: 1;
		transform: scale(1);
	}
</style>
