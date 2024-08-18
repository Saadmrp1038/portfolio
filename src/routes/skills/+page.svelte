<script>
	import Icon from 'svelte-awesome';
	import {
		faJava,
		faPython,
		faJs,
		faReact,
		faNodeJs,
		faDocker,
		faGit
	} from '@fortawesome/free-brands-svg-icons';
	import {
		faCode,
		faServer,
		faDatabase,
		faMobileAlt,
		faTools,
		faBrain,
		faUsers,
		faCodeBranch,
		faCogs,
		faChartLine,
		faTasks,
		faDatabase as faDb,
		faRobot,
		faLightbulb as faSolidLightbulb,
		faBrain as faSolidBrain
	} from '@fortawesome/free-solid-svg-icons';

	// Add Devicon imports
	import cIcon from 'devicon/icons/c/c-original.svg';
	import cppIcon from 'devicon/icons/cplusplus/cplusplus-original.svg';
	import javaIcon from 'devicon/icons/java/java-original.svg';
	import pythonIcon from 'devicon/icons/python/python-original.svg';
	import jsIcon from 'devicon/icons/javascript/javascript-original.svg';
	import typescriptIcon from 'devicon/icons/typescript/typescript-original.svg';
	import reactIcon from 'devicon/icons/react/react-original.svg';
	import svelteIcon from 'devicon/icons/svelte/svelte-original.svg';
	import nodejsIcon from 'devicon/icons/nodejs/nodejs-original.svg';
	import springIcon from 'devicon/icons/spring/spring-original.svg';
	import postgresqlIcon from 'devicon/icons/postgresql/postgresql-original.svg';
	import mysqlIcon from 'devicon/icons/mysql/mysql-original.svg';
	import oracleIcon from 'devicon/icons/oracle/oracle-original.svg';
	import flutterIcon from 'devicon/icons/flutter/flutter-original.svg';
	import opencvIcon from 'devicon/icons/opencv/opencv-original.svg';
	import dockerIcon from 'devicon/icons/docker/docker-original.svg';
	import gitIcon from 'devicon/icons/git/git-original.svg';
	import supabaseIcon from 'devicon/icons/supabase/supabase-original.svg';
	import seleniumIcon from 'devicon/icons/selenium/selenium-original.svg';
	import fastAPIIcon from 'devicon/icons/fastapi/fastapi-original.svg';
	import sqlalchemyIcon from 'devicon/icons/sqlalchemy/sqlalchemy-original.svg';
	import expressIcon from 'devicon/icons/express/express-original.svg';

	import { onMount } from 'svelte';
	import { fade, fly } from 'svelte/transition';
	import { quintOut } from 'svelte/easing';

	const skillIcons = {
		'C/C++': { type: 'devicon', icon: cppIcon }, // Use C++ icon for C/C++
		Java: { type: 'devicon', icon: javaIcon },
		Python: { type: 'devicon', icon: pythonIcon },
		JavaScript: { type: 'devicon', icon: jsIcon },
		TypeScript: { type: 'devicon', icon: typescriptIcon },
		React: { type: 'devicon', icon: reactIcon },
		'Svelte/Sveltekit': { type: 'devicon', icon: svelteIcon },
		'Node.js': { type: 'devicon', icon: nodejsIcon },
		Express: { type: 'devicon', icon: expressIcon },
		'Spring Boot': { type: 'devicon', icon: springIcon },
		PostgreSQL: { type: 'devicon', icon: postgresqlIcon },
		MySQL: { type: 'devicon', icon: mysqlIcon },
		Oracle: { type: 'devicon', icon: oracleIcon },
		Supabase: { type: 'devicon', icon: supabaseIcon },
		Flutter: { type: 'devicon', icon: flutterIcon },
		Git: { type: 'devicon', icon: gitIcon },
		Docker: { type: 'devicon', icon: dockerIcon },
		'OpenAI API': faSolidLightbulb, // No Devicon, using FontAwesome
		Selenium: { type: 'devicon', icon: seleniumIcon },
		'Machine Learning': faRobot, // No Devicon, using FontAwesome
		OpenCV: { type: 'devicon', icon: opencvIcon },
		'Natural Language Processing': faSolidBrain, // No Devicon, using FontAwesome
		Algorithms: faCodeBranch, // No Devicon, using FontAwesome
		'Data Structures': faCodeBranch, // No Devicon, using FontAwesome
		Optimization: faChartLine, // No Devicon, using FontAwesome
		'Critical Thinking': faSolidBrain, // No Devicon, using FontAwesome
		'Problem Solving': faTasks, // No Devicon, using FontAwesome
		'Team Player': faUsers, // No Devicon, using FontAwesome
		FastAPI: { type: 'devicon', icon: fastAPIIcon },
		SQLAlchemy: { type: 'devicon', icon: sqlalchemyIcon }
	};

	const skillCategories = [
		{
			name: 'Programming',
			icon: faCode,
			color: 'bg-blue-500',
			skills: ['C/C++', 'Java', 'Python', 'JavaScript', 'TypeScript']
		},
		{
			name: 'Web Dev',
			icon: faServer,
			color: 'bg-green-500',
			skills: [
				'React',
				'Svelte/Sveltekit',
				'Node.js',
				'Express',
				'Spring Boot',
				'FastAPI',
				'SQLAlchemy'
			]
		},
		{
			name: 'Databases',
			icon: faDatabase,
			color: 'bg-yellow-500',
			skills: ['PostgreSQL', 'MySQL', 'Oracle', 'Supabase']
		},
		{
			name: 'Mobile',
			icon: faMobileAlt,
			color: 'bg-red-500',
			skills: ['Flutter']
		},
		{
			name: 'Tools',
			icon: faTools,
			color: 'bg-purple-500',
			skills: ['Git', 'Docker', 'OpenAI API', 'Selenium']
		},
		{
			name: 'Soft Skills',
			icon: faBrain,
			color: 'bg-pink-500',
			skills: ['Critical Thinking', 'Problem Solving', 'Team Player']
		},
		{
			name: 'AI & ML',
			icon: faSolidLightbulb,
			color: 'bg-indigo-500',
			skills: ['Machine Learning', 'OpenCV', 'Natural Language Processing']
		},
		{
			name: 'Competitive',
			icon: faChartLine,
			color: 'bg-orange-500',
			skills: ['Algorithms', 'Data Structures', 'Optimization']
		}
	];

	let mounted = false;

	onMount(() => {
		mounted = true;
	});
</script>

<svelte:head>
	<title>Skills - Saad Mohammad Rafid Pial</title>
	<link
		href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700&display=swap"
		rel="stylesheet"
	/>
</svelte:head>

<div class="container mx-auto px-2 sm:px-4 py-4 sm:py-8">
	<h1 class="text-4xl font-bold mb-12 text-center text-white font-poppins">My Skills</h1>

	<div
		class="bg-gradient-to-br from-gray-900 via-slate-800 to-gray-900 container mx-auto px-4 py-16 relative z-10"
	>
		<p
			class="text-xl text-center text-slate-300 mb-16 font-light max-w-2xl mx-auto"
			in:fade={{ duration: 1000, delay: 600 }}
		>
			A comprehensive overview of my technical expertise, honed through projects, competitions, and
			coursework at BUET
		</p>

		<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
			{#each skillCategories as category, i}
				{#if mounted}
					<div
						in:fly={{ y: 50, duration: 800, delay: i * 100, easing: quintOut }}
						class="bg-slate-800 rounded-xl overflow-hidden shadow-lg transition-all duration-300 hover:shadow-2xl hover:scale-105 border border-slate-700"
					>
						<div class={`${category.color} p-6 flex items-center`}>
							<Icon data={category.icon} scale={2} class="text-white mr-4" />
							<h3 class="text-2xl font-semibold text-white">{category.name}</h3>
						</div>
						<div class="p-6">
							<ul class="space-y-3">
								{#each category.skills as skill}
									<li
										class="text-slate-300 bg-slate-700 rounded-lg px-4 py-3 text-base flex items-center transition-all duration-200 hover:bg-slate-600"
									>
										{#if typeof skillIcons[skill] === 'object' && skillIcons[skill].type === 'devicon'}
											<img src={skillIcons[skill].icon} alt={skill} class="mr-3 w-6 h-6" />
										{:else}
											<Icon data={skillIcons[skill] || faCode} scale={1.2} class="mr-3" />
										{/if}
										<span class="font-medium">{skill}</span>
									</li>
								{/each}
							</ul>
						</div>
					</div>
				{/if}
			{/each}
		</div>
	</div>
</div>

<style>
	:global(body) {
		font-family: 'Inter', sans-serif;
	}

	.bg-grid-pattern {
		background-image: linear-gradient(to right, rgba(255, 255, 255, 0.1) 1px, transparent 1px),
			linear-gradient(to bottom, rgba(255, 255, 255, 0.1) 1px, transparent 1px);
		background-size: 50px 50px;
	}

	.font-inter {
		font-family: 'Inter', sans-serif;
	}
</style>
