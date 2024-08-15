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
  import supabaseIcon from 'devicon/icons/supabase/supabase-original.svg'
  import seleniumIcon from 'devicon/icons/selenium/selenium-original.svg'
  import fastAPIIcon from 'devicon/icons/fastapi/fastapi-original.svg'
  import sqlalchemyIcon from 'devicon/icons/sqlalchemy/sqlalchemy-original.svg'
  import expressIcon from 'devicon/icons/express/express-original.svg'

  const skillIcons = {
    "C/C++": { type: 'devicon', icon: cppIcon },  // Use C++ icon for C/C++
    "Java": { type: 'devicon', icon: javaIcon },
    "Python": { type: 'devicon', icon: pythonIcon },
    "JavaScript": { type: 'devicon', icon: jsIcon },
    "TypeScript": { type: 'devicon', icon: typescriptIcon },
    "React": { type: 'devicon', icon: reactIcon },
    "Svelte/Sveltekit": { type: 'devicon', icon: svelteIcon },
    "Node.js": { type: 'devicon', icon: nodejsIcon },
    "Express": { type: 'devicon', icon: expressIcon },
    "Spring Boot": { type: 'devicon', icon: springIcon },
    "PostgreSQL": { type: 'devicon', icon: postgresqlIcon },
    "MySQL": { type: 'devicon', icon: mysqlIcon },
    "Oracle": { type: 'devicon', icon: oracleIcon },
    "Supabase": { type: 'devicon', icon: supabaseIcon },
    "Flutter": { type: 'devicon', icon: flutterIcon },
    "Git": { type: 'devicon', icon: gitIcon },
    "Docker": { type: 'devicon', icon: dockerIcon },
    "OpenAI API": faSolidLightbulb,  // No Devicon, using FontAwesome
    "Selenium": { type: 'devicon', icon: seleniumIcon },
    "Machine Learning": faRobot,  // No Devicon, using FontAwesome
    "OpenCV": { type: 'devicon', icon: opencvIcon },
    "Natural Language Processing": faSolidBrain,  // No Devicon, using FontAwesome
    "Algorithms": faCodeBranch,  // No Devicon, using FontAwesome
    "Data Structures": faCodeBranch,  // No Devicon, using FontAwesome
    "Optimization": faChartLine,  // No Devicon, using FontAwesome
    "Critical Thinking": faSolidBrain,  // No Devicon, using FontAwesome
    "Problem Solving": faTasks,  // No Devicon, using FontAwesome
    "Team Player": faUsers,  // No Devicon, using FontAwesome
	"FastAPI": { type: 'devicon', icon: fastAPIIcon },
	"SQLAlchemy": { type: 'devicon', icon: sqlalchemyIcon },
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
			skills: ['React', 'Svelte/Sveltekit', 'Node.js', 'Express', 'Spring Boot','FastAPI','SQLAlchemy']
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
</script>

<svelte:head>
	<title>Skills - Saad Mohammad Rafid Pial</title>
</svelte:head>

<div class="container mx-auto px-6 py-12 bg-gradient-to-br from-gray-900 to-slate-800">
	<h1 class="text-4xl font-bold mb-12 text-center text-white font-poppins">My Skills</h1>

	<div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
		{#each skillCategories as category}
			<div
				class="bg-slate-800 rounded-lg overflow-hidden shadow-lg transition-all duration-300 hover:shadow-2xl hover:scale-105"
			>
				<div class={`${category.color} p-4 flex items-center`}>
					<Icon data={category.icon} scale={1.5} class="text-white mr-4 animate-pulse" />
					<h3 class="text-xl font-bold text-white">{category.name}</h3>
				</div>
				<div class="p-4">
					<ul class="space-y-2">
						{#each category.skills as skill}
							<li class="text-slate-300 bg-slate-700 rounded px-3 py-2 text-sm flex items-center">
								{#if typeof skillIcons[skill] === 'object' && skillIcons[skill].type === 'devicon'}
									<img src={skillIcons[skill].icon} alt={skill} class="mr-2 w-6 h-6" />
								{:else}
									<Icon data={skillIcons[skill] || faCode} scale={1} class="mr-2" />
								{/if}
								{skill}
							</li>
						{/each}
					</ul>
				</div>
			</div>
		{/each}
	</div>

	<div class="mt-12 text-center text-slate-300">
		<p>
			These skills have been developed through various projects, competitions, and coursework at
			BUET.
		</p>
	</div>
</div>

<style>
	:global(body) {
		font-family: 'Inter', sans-serif;
	}
	.font-poppins {
		font-family: 'Poppins', sans-serif;
	}
	@keyframes gradient {
		0% {background-position: 0% 50%;}
		50% {background-position: 100% 50%;}
		100% {background-position: 0% 50%;}
	}
	.bg-gradient-to-br {
		background-size: 200% 200%;
		animation: gradient 15s ease infinite;
	}
</style>