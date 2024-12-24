<script lang="ts">
	import { cn } from '$lib/utils/cn';
    import { useViewportScroll, useTransform, Motion } from 'svelte-motion';
	let randomMove = () => Math.random() * 4 - 2;

    import earth from '$lib/assets/earth.png';
    import moon from '$lib/assets/moon.png';
    import mars from '$lib/assets/mars.png';
    import jupiter from '$lib/assets/jupiter.webp';
    import saturn from '$lib/assets/saturn.png';
    import uranus from '$lib/assets/uranus.png';
    import neptune from '$lib/assets/neptune.png';
    import galaxy from '$lib/assets/galaxy.png';
    import meteor from '$lib/assets/meteor.png';
    import blackhole from '$lib/assets/blackhole.webp';
    import asteroid from '$lib/assets/asteroid.png';

	export let minSize: number = 0.6;
	export let maxSize: number = 1.8;
	export let speed: number = 400;
	export let particleDensity: number | undefined = 400;
	export let className: string | undefined = undefined;

    export let starColors = ['#a87bff', '#fffa86', '#a6a8ff', '#ffa371', '#ffd27d', '#ff7f7f', '#7fff7f', '#7f7fff', '#ff7fff', '#7fffff', '#ffffff']
    function getRandomColor () {
        return starColors[Math.floor(Math.random() * starColors.length)]
    }

	function getRandomValue() {
		return minSize + Math.random() * (maxSize - minSize);
	}


    export let redStarColors = ['#4E0707', '#900D09', '#C41E1E', '#FF0000', '#FF4D4D', '#FF7A7A', '#FFA5A5', '#FFCCCC', '#FFE6E6', '#FFF2F2']
    function getRandomRedColor () {
        return redStarColors[Math.floor(Math.random() * redStarColors.length)]
    }
    export let redParticleDensity: number | undefined = 1000;

    export let greenStarColors = ['#0A4E0A', '#0D900D', '#1EC41E', '#00FF00', '#4DFF4D', '#7AFF7A', '#A5FFA5', '#CCFFCC', '#E6FFE6', '#F2FFF2']
    function getRandomGreenColor () {
        return greenStarColors[Math.floor(Math.random() * greenStarColors.length)]
    }
    export let greenParticleDensity: number | undefined = 100;

    export let blueStarColors = ['#07074E', '#0D0D90', '#1E1EC4', '#0000FF', '#4D4DFF', '#7A7AFF', '#A5A5FF', '#CCCCFF', '#E6E6FF', '#F2F2FF']
    function getRandomBlueColor () {
        return blueStarColors[Math.floor(Math.random() * blueStarColors.length)]
    }
    export let blueParticleDensity: number | undefined = 1000;

    const { scrollYProgress } = useViewportScroll();

    const translateRed = useTransform(scrollYProgress, [0, 1], [0, 4000]);
	const translateGreen = useTransform(scrollYProgress, [0, 1], [0, 3000]);
	const translateBlue = useTransform(scrollYProgress, [0, 1], [0, 1000]);

</script>

<!-- Column -->
<div class='bg-black h-[10000px] w-full text-white m-0 p-0 justify-center items-center flex-col'>
    <!-- Background moving layer -->
    <div class={cn('relative h-full w-full', className)}>
        <div class="absolute inset-0">
            {#each [...Array(particleDensity)] as _, i (`star-${i}`)}
                <Motion
                    let:motion
                    animate={{
                        top: `calc(${Math.random() * 100}% + ${randomMove()}px)`,
                        left: `calc(${Math.random() * 100}% + ${randomMove()}px)`,
                        opacity: Math.random(),
                        scale: [1, 1.2, 0]
                    }}
                    transition={{
                        duration: Math.random() * 10 + speed,
                        repeat: Infinity,
                        ease: 'linear'
                    }}
                >
                    <span
                        use:motion
                        class="inline-block"
                        style={`position: absolute; width: ${getRandomValue()}px; height: ${getRandomValue()}px; background-color: ${getRandomColor()}; border-radius: 50%; top: ${Math.random() * 100}%; left: ${Math.random() * 100}%;`}
                    ></span>
                </Motion>
            {/each}
        </div>
    </div>
    <!-- Background stationary layer -->
    <div class={cn('absolute top-0 h-[10000px] w-full', className)}>
        <Motion let:motion style={{ y: translateBlue }}>
            <div class="absolute inset-0" use:motion>
                {#each [...Array(blueParticleDensity)] as _, i (`stationary-star-${i}`)}
                    <span
                        class="inline-block"
                        style={`z-index: 100; position: absolute; width: ${getRandomValue()}px; height: ${getRandomValue()}px; background-color: ${getRandomBlueColor()}; border-radius: 50%; top: ${Math.random() * 100}%; left: ${Math.random() * 100}%;`}
                    ></span>
                {/each}
            </div>
        </Motion>
        <Motion let:motion style={{ y: translateGreen }}>
            <div class="absolute inset-0" use:motion>
                {#each [...Array(greenParticleDensity)] as _, i (`stationary-star-${i}`)}
                    <span
                        class="inline-block"
                        style={`z-index: 100; position: absolute; width: ${getRandomValue()}px; height: ${getRandomValue()}px; background-color: ${getRandomGreenColor()}; border-radius: 50%; top: ${Math.random() * 100}%; left: ${Math.random() * 100}%;`}
                    ></span>
                {/each}
            </div>
        </Motion>
        <Motion let:motion style={{ y: translateRed }}>
            <div class="absolute inset-0" use:motion>
                {#each [...Array(redParticleDensity)] as _, i (`stationary-star-${i}`)}
                    <span
                        class="inline-block"
                        style={`z-index: 100; position: absolute; width: ${getRandomValue()}px; height: ${getRandomValue()}px; background-color: ${getRandomRedColor()}; border-radius: 50%; top: ${Math.random() * 100}%; left: ${Math.random() * 100}%;`}
                    ></span>
                {/each}
            </div>
        </Motion>
    </div> 
    <!-- Stationary Planet Layer -->
    <!-- font: -->
    <div class='absolute top-0 h-[11000px] w-full text-[#A9f9f9] m-0 p-0 justify-center items-center flex-col text-center'>
        <h1 class='pt-[100px] text-2xl' style="font-family: Georgia;">To The Love Of My Life</h1>

        <!-- Earth -->
        <img src={earth} class='w-[50px] h-[50px] mt-[100px] m-0 mx-auto' alt='earth' />
        <p class='pt-[20px] text-l' style="font-family: Georgia;">
            I love you from Earth, where we first met,<br>
        </p>
        <p class='pt-[200px] text-l' style="font-family: Georgia;">
            To the moon's soft glow, where dreams are set.<br>
        </p>
        <img src={moon} class='w-[24px] h-[24px] mt-[12px] m-0 mx-auto' alt='moon' />
        <p class='pt-[300px] text-l' style="font-family: Georgia;">
            Through the night skies, stars shining bright,<br>
            Our love ascends in celestial flight.
        </p>

        <img src={mars} class='w-[50px] h-[50px] mt-[400px] m-0 mx-auto' alt='mars' />

        <p class='pt-[20px] text-l' style="font-family: Georgia;">
            To Mars, the red jewel in the velvet sky,<br>
            Our hearts intertwined as the planets sigh.<br>
        </p>
        <p class='pt-[500px] text-l' style="font-family: Georgia;">
            Past the asteroid belts, where comets roam,<br>
            Our love as vast as the cosmic foam.<br>
        </p>
        <img src={asteroid} class='w-full mt-[10px] m-0 mx-auto' alt='asteroid' />
        <img src={jupiter} class='w-[70px] h-[70px] mt-[400px] m-0 mx-auto' alt='jupiter' />
        <img src={saturn} class='h-[60px] w-auto mt-[500px] m-0 mx-auto' alt='saturn' />
        <p class='pt-[20px] text-l' style="font-family: Georgia;">
            Beyond Jupiter’s storms and Saturn’s rings,<br>
            My love for you, a symphony that sings.
        </p>    
        <img src={uranus} class='w-[40px] h-[40px] mt-[800px] m-0 mx-auto' alt='uranus' />
        <p class='pt-[600px] text-l' style="font-family: Georgia;">
            To the icy realms of Neptune’s seas,<br>
        </p>
        <img src={neptune} class='w-[40px] h-[40px] mt-[20px] m-0 mx-auto' alt='neptune' />
        <p class='pt-[20px] text-l' style="font-family: Georgia;">
            Our love as boundless as galaxies.
        </p>

        <p class='pt-[1800px] text-l' style="font-family: Georgia;">
            And further still, past the known, the seen,<br>
            To JADES-GS-z13-0, where light has been.<br>
        </p>
        <img src={galaxy} class='w-full h-auto mt-[-50px] m-0 mx-auto' alt='galaxy' />
        <p class='pt-[1800px] text-l' style="font-family: Georgia;">
            Beyond the universe’s final crest,<br>
            Our love expands, forever blessed.
        </p>

        <p class='pt-[1050px] text-l' style="font-family: Georgia;">
            Through the endless void, where time stands still,<br>
            My love for you, a boundless thrill.
        </p>
        <p class='pt-[130px] text-l text-black' style="font-family: Georgia;">
            To the edge of space and then beyond,<br>
            My heart with yours eternally bonds.
        </p>

        <p class='pt-[3500px] pb-[400px] text-l text-black' style="font-family: Georgia;">
            And back again, through the cosmic sea,<br>
            To the place where you and I will be.<br>
            Our love, a journey without end,<br>
            To you, my life, my heart I send.
        </p>
    </div>
</div>
