<template>
  	<main v-if="!loading" id="hello">

    	<!-- gradients -->
    	<div class="css-blurry-gradient-blue"></div>
    	<div class="css-blurry-gradient-green"></div>

		<section data-aos="fade-in" id="hero" class="hero">
		
			<div class="head">
				<span>
					Hi all, I am
				</span>
				<h1>{{ config.dev.name }}</h1>
        <span class="diple flex">
          >&nbsp;
				<h2 class="line-1 anim-typewriter max-w-fit"> {{ config.dev.role }} </h2>
        </span>
			</div>
      <div>
      </div>
			<div id="info">
				<span class="action">
					// complete the game to continue
				</span>
				<span :class="{hide: isMobile}">
					// you can also see it on my Github page
				</span>
				<span :class="{hide: !isMobile}">
					// find my profile on Github:
				</span>
				<p class="code">
					<span class="identifier">
						const
					</span>
					<span class="variable-name">
						githubLink
					</span>
					<span class="operator">
						=
					</span>
					<a class="string" :href="'https://github.com/' + config.public.dev.contacts.social.github.user">
						"https://github.com/{{ config.public.dev.contacts.social.github.user }}"
					</a>
				</p>
			</div>
		</section>

		<section data-aos="fade-up" class="game" v-if="!isMobile">
			<SnakeGame />
		</section>
<!-- 
    <section id="mobile-game" class="mobile-game">
			<SnakeGameMobile />
		</section> -->

	</main>
</template>

<style>

#hello {
  display: flex;
  height: 100%;
  width: 100%;
  flex: 1 1 auto;
  padding-left: 275px;
}

.hero {
	width: 100%;
	justify-content: center;
}

.game {
	display: flex;
	flex-direction: column;
	width: 100%;
	height: 100%;
	justify-content: center;
	z-index: 20;
}

.mobile-game {
	display: none;
    position: relative;
	flex-direction: column;
	width: 100%;
	height: 100%;
	justify-content: center;
	z-index: 30;
}

#hello .hero {
	display: flex;
	flex-direction: column;
	margin: 0rem;
}

#hello .head span {
  font-size: 18px;
  line-height: 1;
  color: #E5E9F0;
  font-family: 'Fira Code Retina';
}

#hello .head h1 {
  font-size: 58px;
  line-height: 1;
  color: #E5E9F0;
  font-family: 'Fira Code Regular';
  padding-top: 1rem; /* 16px */
  padding-bottom: 1rem; /* 16px */
}

#hello .head h2, #hello .head .diple {
  font-size: 32px;
  line-height: 1;
  color: #4D5BCE;
  font-family: 'Fira Code Retina';
}

.head {
  padding-bottom: 3rem;
}

#info {
	display: flex;
	flex-direction: column;
}

#info > span {
    font-size: 14px;
    line-height: 1;
    color: #607B96;
    font-family: 'Fira Code Retina';
    padding-bottom: 1rem; /* 16px */
}

.code {
    font-family: 'Fira Code Medium';
    color: #E5E9F0;
}

.code .identifier {
  color: #4D5BCE;
}

.code .variable-name {
  color: #43D9AD;
}

.code .operator {
  color: white;
}

.code .string {
  color: #E99287;
  text-decoration-line: underline;
  text-underline-offset: 4px;
}

#info {
	padding-block: 2.5rem;
    font-size: 14px;
}

#info .action {
	display: flex
}

.hide {
  display: none;
}

/* Typewrite Animation */

.line-1 {
    width: fit-content;
    border-right: 3px solid rgba(255,255,255,.75);
    white-space: nowrap;
    overflow: hidden;
    padding-right: 2px;
}

.anim-typewriter{
    animation: typewriter 3.5s steps(40) 1s 1 normal both,
    blinkTextCursor 800ms steps(40) infinite normal;
}

@keyframes typewriter{
  from{width: 0;}
  to{width: 100%;}
}

@keyframes blinkTextCursor{
  from{border-right-color: rgba(255,255,255,.75);}
  to{border-right-color: transparent;}
}

/* Background blur */

.css-blurry-gradient-blue {
    position: fixed;
    bottom: 25%;
    right: 5%;
    width: 300px;
    height: 300px;
	border-radius: 0% 0% 50% 50%;
    rotate: 10deg;
	filter: blur(70px);
    background: radial-gradient(circle at 50% 50%,rgba(77, 91, 206, 1), rgba(76, 0, 255, 0));
    opacity: 0.5;
    z-index: 10;
}

.css-blurry-gradient-green {
  position: absolute;
  top: 20%;
  right: 30%;
  width: 300px;
  height: 300px;
	border-radius: 0% 50% 0% 50%;
	filter: blur(70px);
  background: radial-gradient(circle at 50% 50%,rgba(67, 217, 173, 1), rgba(76, 0, 255, 0));
  opacity: 0.5;
  z-index: 10;
}

/* Mobile */
@media (max-width: 768px) {

	#hello {
		padding-left: 0;
	}

	#hello .hero {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		margin: 1.75rem; /* 28px */
	}
	.head {
		padding-top: 4rem; /* 40px */
	}

	#hello .head h2, #hello .head .diple {
		font-size: 20px;
		color: #43D9AD;
	}
	
	#info .action {
		display: none;
	}
}

/* Tablet */
@media (min-width: 768px) and (max-width: 1024px) {

	#hello {
		padding-left: 0;
	}

	#hello .hero {
		display: flex;
		flex-direction: column;
		justify-content: center;
		margin: 1.75rem; /* 28px */
	}

	.head {
		padding-top: 4rem; /* 40px */
	}
}

@media (min-width: 1024px) and (max-width: 1320px) {

	#hello {
		padding-left: 135px;
	}
}


/* Desktop */

@media (min-width: 1024px) {

    .css-blurry-gradient-blue {
        position: fixed;
        bottom: 10%;
        right: 10%;
        width: 500px;
        height: 500px;
        opacity: 0.7;
        border-radius: 100% 50% 100% 0%;
    }

    .css-blurry-gradient-green {
        position: fixed;
        top: 10%;
        right: 35%;
        filter: blur(100px);
        rotate: 10deg;
        width: 400px;
        height: 400px;
        opacity: 0.5;
        border-radius: 100% 0% 0% 0%;
        rotate: 20deg;
    }
}

/* Desktop 2K */

@media (min-width: 1920px){

	#hello {
		padding-left: 310px;
	}

	#hello .head h1 {
		font-size: 62px;
	}
}

</style>

<script>
export default {
    name: 'Hello',
    setup() {
        const config = useRuntimeConfig()
        return {
            config
        }
    },
    data() {
        return {
            isMobile: false,
            loading: true
        }
    },
    mounted() {
        // Detectamos si es mobile
        if (window.innerWidth <= 1024) {
            this.isMobile = true
        }

        // Listen resize window event
        window.addEventListener('resize', this.handleResize)

        // When the component is mounted, remove the loader.
        this.loading = false
    },
    beforeDestroy() {
        // Remove the event listener when the component is destroyed.
        window.removeEventListener('resize', this.handleResize)
    },
    methods: {
        handleResize() {
            if (window.innerWidth <= 1024) {
                this.isMobile = true
            } else {
                this.isMobile = false
            }
        },
        showGame(){
            const snake = document.getElementById('mobile-game')
            const hero = document.getElementById('hero')
            hero.style.display = 'block' ? hero.style.display = 'none' : hero.style.display = 'block'
            snake.style.display = 'none' ? snake.style.display = 'block' : snake.style.display = 'none'
        }
    }
}
</script>

