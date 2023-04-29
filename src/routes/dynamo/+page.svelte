<script lang="js">
	export const ssr = false;
	import { onMount } from "svelte";

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
	<img
		src="John.jpg"
		class="john"
	/>
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
</div>
