<html>
  <head
    <style>
    // todo: heavy refactoring

body {
	display: grid;
	justify-content: center;
	align-content: center;
	height: 100vh;
	
	overflow: hidden;
	background: #dadada;
	
	@media screen and (max-width: 1000px) {
		transform: scale(0.9);
	}
	
	@media screen and (max-width: 600px) {
		transform: scale(0.6);
	}
}

@function ease($t, $b, $c, $d) {
	// https://spicyyoghurt.com/tools/easing-functions
	// sine ease-out
	@return (-1 * $c) / 2 * (cos($PI * $t / $d) - 1) + $b;
}

@mixin rotated-text($num-letters: 14, $angle-span: 360deg, $kern: ()) {
	$angle-per-char: $angle-span / $num-letters;
	@for $i from 0 through $num-letters {
		$angle: $angle-per-char * $i;
		@if (map-has-key($kern, $i)) { $angle: map-get($kern, $i); }
		
		& > *[data-idx='#{$i}'] {
			height: 245px;
			transform: rotate($angle) scaleX(0.95);
			transform-origin: bottom center;
			line-height: 0;
		}
	}
}

.text {
	font-size: 6.5rem;
	font-family: Kanit, sans-serif;
	text-transform: uppercase;

	color: white;
	text-stroke: 2px var(--shadow-color, #282828);
	-webkit-text-stroke: 2px var(--shadow-color, #282828);
	letter-spacing: 3px;
	transform: scaleX(0.5);
	
	$shadows: 30;
	$steps: 25;
	animation: stagger 2.5s steps($steps) alternate infinite;

	@keyframes stagger {
		// for each time-step ($i/$step) of the animation...
		@for $i from 0 through $steps {
			$timestep: $i / $steps;
			
			// generate the layer of text shadows for each step of
			// the anim, placing each layer at some x-position using
			// an easing fn for the current time-step
			$text-shadow: null;
			@for $j from 1 through $shadows {
				$shadowstep: $j / $shadows;
				
				$text-shadow: (
					$text-shadow 
					#{ease($timestep, (-10px*$shadowstep), (20px*$shadowstep), 1)} (0.3px*$j) var(--shadow-color, #282828)
					#{if($j != $shadows, ',', '')}
				)
			}
			
			#{$timestep * 100}% {
				text-shadow: $text-shadow;
			}
		}
	}
}

.circular {
	width: 240px;
	height: 240px;
	border-radius: 100%;
	
	position: absolute;
	top: 50%;
	left: 50%;
	transform: translate(-50%, -50%) scale(var(--scale, 1));
	& > * {
		position: absolute;
		top: -50%; left: 33%;
	}
	
	@include rotated-text(22, 360deg, (
		1: 19deg,
		5: 81deg,
		6: 99deg,
		7: 117deg,
		8: 134deg,
		10: 154deg,
		12: 185deg,
		13: 205deg,
		15: 238deg,
		16: 257deg,
		17: 276deg,
		21: 337deg
	));
	
	&--solid {
		--scale: 0.9;
		--shadow-color: #d5d5d5;

		.text { color: var(--shadow-color); 	}
	}
}

.rotate {
	--delay: 0;
	
	animation: rotate 5s ease-in-out alternate infinite;
	animation-delay: var(--delay);
	@keyframes rotate {
		100% { transform: rotate(360deg); }
	}
}
  </style>
  </head>
const word = 'HELLOW CODERS • WELCOME HERE •'

div.rotate
	div.circular.circular--solid(style='--shadow-color: #ababab; filter: blur(1px); opacity: 0.7;')
		each char, i in word.split('')
			span.text(data-idx=i)= char

div.rotate
	div.circular
		each char, i in word.split('')
			span.text(data-idx=i)= char

</html>



Hello Coders! Welcome to my GitHub profile. I am a 3rd-year Computer Science Engineering student specializing in full-stack development and mobile app development.

Below are some of my skills and contact details:

## Skills


- ![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E)
- ![React](https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB)
- 	![React Native](https://img.shields.io/badge/react_native-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB)
- 	![React Hook Form](https://img.shields.io/badge/React%20Hook%20Form-%23EC5990.svg?style=for-the-badge&logo=reacthookform&logoColor=white)
- 	![Redux](https://img.shields.io/badge/redux-%23593d88.svg?style=for-the-badge&logo=redux&logoColor=white)
- 	![React Router](https://img.shields.io/badge/React_Router-CA4245?style=for-the-badge&logo=react-router&logoColor=white)
- ![Java](https://img.shields.io/badge/java-%23ED8B00.svg?style=for-the-badge&logo=openjdk&logoColor=white)
- ![HTML5](https://img.shields.io/badge/html5-%23E34F26.svg?style=for-the-badge&logo=html5&logoColor=white)
- ![PHP](https://img.shields.io/badge/php-%23777BB4.svg?style=for-the-badge&logo=php&logoColor=white)
- ![TailwindCSS](https://img.shields.io/badge/tailwindcss-%2338B2AC.svg?style=for-the-badge&logo=tailwind-css&logoColor=white)
- ![Bootstrap](https://img.shields.io/badge/bootstrap-%238511FA.svg?style=for-the-badge&logo=bootstrap&logoColor=white)
- ![NodeJS](https://img.shields.io/badge/node.js-6DA55F?style=for-the-badge&logo=node.js&logoColor=white)
- ![MySQL](https://img.shields.io/badge/mysql-4479A1.svg?style=for-the-badge&logo=mysql&logoColor=white)
- ![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
- ![Google Cloud](https://img.shields.io/badge/GoogleCloud-%234285F4.svg?style=for-the-badge&logo=google-cloud&logoColor=white)
- ![Netlify](https://img.shields.io/badge/netlify-%23000000.svg?style=for-the-badge&logo=netlify&logoColor=#00C7B7)
- ![Oracle](https://img.shields.io/badge/Oracle-F80000?style=for-the-badge&logo=oracle&logoColor=white)
- ![C](https://img.shields.io/badge/c-%2300599C.svg?style=for-the-badge&logo=c&logoColor=white)

## Contact Details

- Email: ak47akm1610@gmail.com
- Instagram: [akm_16.10](https://www.instagram.com/akm_16.10/)
- LinkedIn: [Anand Kr Maurya](https://www.linkedin.com/in/anand-kr-maurya-akm16)
- Twitter: [Anand Kr Maurya](https://twitter.com/Anand786akm)

## My Portfolio

https://myportfolio-1610.netlify.app/

Feel free to reach out to me for collaborations, projects, or just to say hello!

