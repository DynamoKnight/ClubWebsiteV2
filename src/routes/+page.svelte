<svelte:head>
	<title>A cool website that is yet to have a title...</title>
</svelte:head>
<h1 class="my-10 text-center text-6xl font-extrabold md:text-7xl">Computer Science!</h1>
<div class="grid grid-cols-1 space-y-10 md:grid-cols-2 md:space-y-0 lg:grid-cols-3 lg:space-x-10">
	<div class="card">
		<h2>Item Title</h2>
		<p>
			Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aliquam consequatur, dicta, eos, ex
			hic inventore laboriosam quae qui quo recusandae tempore ullam voluptatum! Accusamus ea
			excepturi modi quidem repellat vero?
		</p>
	</div>
	<div class="card">
		<h2>Item Title</h2>
		<p>
			Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aliquam consequatur, dicta, eos, ex
			hic inventore laboriosam quae qui quo recusandae tempore ullam voluptatum! Accusamus ea
			excepturi modi quidem repellat vero?
		</p>
	</div>
	<div class="card">
		<h2>Item Title</h2>
		<p>
			Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aliquam consequatur, dicta, eos, ex
			hic inventore laboriosam quae qui quo recusandae tempore ullam voluptatum! Accusamus ea
			excepturi modi quidem repellat vero?
		</p>
	</div>
</div>

<style lang="postcss">
	.card > h2 {
		@apply mb-2 text-center text-2xl font-bold;
	}
	.card > p {
		@apply text-center;
	}
	.card {
		@apply mx-4 border-2 py-5 px-6 shadow-2xl;
	}
</style>
