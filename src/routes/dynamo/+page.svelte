<svelte:head>
	<title>DynamoKnight</title>
	<link rel="stylesheet" href="https://fonts.googleapis.com/icon?family=Material+Icons">
	<link href="app.js" rel="stylesheet" type="text/js" />
</svelte:head>

<script lang="js">
	// Sets server-side rendering to false, meaning the java code will render on the client rather than the server.
	export const ssr = false;
	import { onMount } from "svelte";
	// Loads js only after the html page is rendered
	onMount(() => {
		// When the duck is clicked it will add the duck to the grapes class to animate
		const duck = document.getElementById("duck");
		const dialogue = document.getElementById("dialogue");
		const shootArea = document.getElementById("comic");

		shootArea.addEventListener("click", function (event) {
			dialogue.innerHTML = "Got Any Grapes?";
			alert("You shot at " + event.x + ". The Duck was at " + duck.getBoundingClientRect().left);

			// Repeatable
			if (duck.className.indexOf(" grapes ") > -1) {
				duck.className = duck.className.replace(" grapes ", ""); // Removes grapes class when clicked again
				dialogue.innerHTML = "Waddle Waddle";
			} else {
				duck.className += " grapes ";
			}
		});

		// The Anonymous Groups
		var slides = [
    {
        "color" : "red",
        "text" : "Alcoholics Anonymous",
        "image" : "liquor",
        "link" : "homeAA.html"
    },
    {
        "color" : "gold",
        "text" : "Emotions Anonymous",
        "image" : "sentiment_neutral",
        "link" : "homeEA.html"
    },
    {
        "color" : "darkorchid",
        "text" : "Gamblers Anonymous",
        "image" : "casino",
        "link" : "homeGA.html"
    },
    {
        "color" : "seagreen",
        "text" : "Narcotics Anonymous",
        "image" : "medication",
        "link" : "homeNA.html"
    },
    {
        "color" : "coral",
        "text" : "Overeaters Anonymous",
        "image" : "lunch_dining",
        "link" : "homeOA.html"
    },
    {
        "color" : "deeppink",
        "text" : "Sex and Love Anonymous",
        "image" : "favorite",
        "link" : "homeSLAA.html"
    },
    {
        "color" : "royalblue",
        "text" : "Workaholics Anonymous",
        "image" : "work",
        "link" : "homeWA.html"
    }
		]

		// Carousel initial values
		var slideNum = 0;
		var prev = document.getElementById("prevbtn");
		var next = document.getElementById("nextbtn");
		var curSlide = document.getElementById("slide" + slideNum);
		var prevSlide = document.getElementById("slide" + (slides.length - 1));
		var nextSlide = document.getElementById("slide" + (slideNum + 1));

		//////////////////////////////////////////
		//// DO STUFF
		//////////////////////////////////////////

		/////////////////////////////////
		// Only on Dynamo Page
		// Initializes the carousels starting appearance
		//window.onload = init();
		var title = document.getElementsByTagName("title");
		if(title[0].innerHTML == "DynamoKnight"){
			for (var i = 0; i < slides.length; i++){
				var slideID = document.getElementById("slide" + (i));
				slideID.style.backgroundColor = slides[i].color;
				slideID.setAttribute("index",i)
				//Google icons
				slideID.innerHTML = slides[i].image;
				slideID.onclick = openWin;
			}
		//Shows the carousel when page first loads
		showCarousel();
		}
		/////////////////////////////////

		//////////////////////////////////////////
		//// FUNCTIONS
		//////////////////////////////////////////

		// Opens a page corresponding with the index of the slide in the array
		function openWin(event){
		var slide = event.target;
		var index = slide.getAttribute("index");
		window.open(slides[index].link,"_self");
		}

		// Sets the positions of the slides
		function showCarousel(){
			//curSlide.style.display = "block";
			curSlide.style.display = "flex";
			curSlide.style.left = "45%";
			curSlide.style.width = "200px";
			curSlide.style.height = "200px";
			curSlide.style.filter = "brightness(100%)";
			curSlide.style.zIndex = "992";
			curSlide.style.fontSize = "200px";
			curSlide.style.alignItems = "center";
			curSlide.style.justifyContent = "center";

			prevSlide.style.display = "flex";
			prevSlide.style.width = "150px";
			prevSlide.style.height = "150px";
			prevSlide.style.filter = "brightness(70%)";
			prevSlide.style.left = "32%";
			prevSlide.style.zIndex = "991";
			prevSlide.style.fontSize = "150px";
			prevSlide.style.alignItems = "center";
			prevSlide.style.justifyContent = "center";

			nextSlide.style.display = "flex";
			nextSlide.style.left = "60%";
			nextSlide.style.width = "150px";
			nextSlide.style.height = "150px";
			nextSlide.style.filter = "brightness(70%)";
			nextSlide.style.fontSize = "150px";
			nextSlide.style.alignItems = "center";
			nextSlide.style.justifyContent = "center";


		}

		// Hides the previous slides
		function hideCarousel(){
			curSlide.style.display = "none";
			prevSlide.style.display = "none";
			nextSlide.style.display = "none";
		}

		// When the next button is clicked
		next.addEventListener('click',function(){
			hideCarousel();
			//It shifts to the next slide
			prevSlide = curSlide;
			curSlide = nextSlide;
			slideNum++;
			//Has to reset to cycle back
			if(slideNum >= slides.length){
				slideNum = 0;
			}
			//The next slide has to cycle back
			if(slideNum == (slides.length - 1)){
				nextSlide = document.getElementById("slide0");
			}
			//The next slide is the one after
			else{
				nextSlide = document.getElementById("slide" + (slideNum + 1));
			}
			showCarousel();

		});
		// When the prev button is clicked
		prev.addEventListener('click',function(){
			hideCarousel();
			//It shifts back to the previous slide
			nextSlide = curSlide;
			curSlide = prevSlide;
			slideNum--;
			//Has to reset to cycle back
			if(slideNum < 0){
				slideNum = slides.length - 1;
			}
			//The prev slide can't be -1
			if(slideNum == 0){
				prevSlide = document.getElementById("slide" + (slides.length - 1));
			}
			//The prev slide is the one before
			else{
				prevSlide = document.getElementById("slide" + (slideNum - 1));
			}
			showCarousel();

		});
	});

</script>

<nav class="title">
	<h1>
		<a href="#"
			><img
				src="/BobaFett.png"
				alt="Logo"
				width="50px"
			/></a
		>Cool Nakul's Website
	</h1>
	<ul>
		<li><a href="app.html">Home</a></li>
		<li><a href="">Explore</a></li>
		<li><a href="">About</a></li>
		<li>
			<a href="">Shop</a>
			<ul>
				<li><a href="">Cards</a></li>
				<li><a href="">Games</a></li>
				<li><a href="">Other</a></li>
			</ul>
		</li>
		<li><a href="dynamo.html">Create Your Own</a></li>
		<li>
			<a
				href=""
				class="money">$0</a
			>
		</li>
	</ul>
</nav>

<div class="resume">
	<img src="John.jpg" class="john" alt = "John Cena"/>
	<div class="bold">
		<h2>Nakul K.</h2>
		<h4>My Resume</h4>
	</div>
	<p>Future President of Computer Science Club</p>
	<p>Mission Statement: Rule the World with html robots!!!</p>
	<ul class="list">
		<li>I play Piano and Badminton.</li>
		<li>I've got a 3.98 GPA! (Darn Algebra 1)</li>
		<li>I am good at creating things, being helpful, working efficiently, and playing games.</li>
	</ul>
	<a
		class="link"
		href="https://pokemon-cards.nakulkumar3.repl.co/cards.html"
	>
		Pokemon Card Website I made!</a
	>
	<p>
		Stuff About Me: I am cool and the reason I am better than everyone else is because lorem ipsum
		dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et
		dolore magna aliqua.
	</p>
</div>

<div class="featured">
	<div
		class="card"
		id="Pikachu"
	>
		<div class="char-name">
			<div class="evolution">Basic</div>
			<div class="name">Pikachu</div>
			<div class="HP">60 HP</div>
			<div>
				<img
					src="/elecType.png"
					alt="Type"
					class="type"
				/>
			</div>
		</div>
		<div class="char-img">
			<img
				src="/pikachu.png"
				alt="Pikachu"
			/>
		</div>

		<div class="meta">NO. 025 Mouse Pokémon. Length: 1'4”,Weight: 13 lbs.</div>

		<div class="container">
			<div class="char-stats">
				<div class="move1">
					<p class="char-move">Charge</p>
					<p>0</p>
				</div>
				<p class="stat">
					Search your deck for 2 energy cards and attach them to this Pokémon. Then shuffle the
					deck.
				</p>

				<div class="move2">
					<p class="char-move">Thunder Bolt</p>
					<p>70</p>
				</div>
				<p class="stat">Discard All energy cards from this Pokémon.</p>
			</div>
		</div>
	</div>

	<div
		class="comic1"
		id="comic"
	>
		<div
			class="duck"
			id="duck"
		>
			<div class="dialogue">
				<p id="dialogue">Waddle Waddle</p>
			</div>
			<div class="head">
				<div class="eye1" />
				<div class="eye2" />
				<div class="beak" />
			</div>
			<div class="foot1" />
			<div class="foot2" />
			<div class="tail" />
		</div>

		<div class="lemonadeStand">
			<div class="supportbeam1" />
			<div class="supportbeam2" />
			<div class="storage">Lemonade</div>
			<div class="sign">Ice Fresh</div>
		</div>
		<div class="man">
			<div class="manHead">
				<div class="manEye1" />
				<div class="manEye2" />
				<div class="manMouth" />
			</div>
		</div>
	</div>

	<div class="carousel">
		<div id="prevbtn"></div>
		<div id="nextbtn"></div>
  
		<i class = "icons" id = "slide0"></i>
		<i class = "icons" id = "slide1"></i>
		<i class = "icons" id = "slide2"></i>
		<i class = "icons" id = "slide3"></i>
		<i class = "icons" id = "slide4"></i>
		<i class = "icons" id = "slide5"></i>
		<i class = "icons" id = "slide6"></i>
  
	 </div>

</div>
