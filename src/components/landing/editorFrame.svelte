<script>
	import { faCss3, faHtml5, faJs } from '@fortawesome/free-brands-svg-icons';
	import Fa from 'svelte-fa';

	export let title;
</script>

<section class="w-full p-2 md:w-[90%] max-w-[1000px]">
	<header>
		<nav>
			<ul>
				<li>
					<div class="flex text-sm gap-1 flex-col">
						<p style="margin-bottom: -7px;" class="text-sm md:text-xl capitalize text-light">
							{title}
						</p>
						<p
							class="text-sky-400 dark:text-sky-300 outline-none focus:outline-sky-300 p-1 focus:dark:outline-sky-400 rounded-lg"
							spellcheck="false"
						>
							<span>by</span>
							<a class="text-light" href={`/nuur`}>@nuur</a>
						</p>
					</div>
				</li>
			</ul>
		</nav>
	</header>
	<div id="main" class="bg-secondary dark:text-secondary dark:bg-secondary-dark">
		<section id="editor">
			<div class="flex gap-2">
				<button class="flex gap-1 items-center justify-center p-2"
					><span class="text-rose-500"><Fa icon={faHtml5} /></span>HTML</button
				>
				<button class="flex gap-1 items-center justify-center p-2">
					<span class="text-blue-500"><Fa icon={faCss3} /></span>CSS
				</button>

				<button class="flex gap-1 items-center justify-center p-2">
					<span class="text-yellow-500"><Fa icon={faJs} /></span>JS
				</button>
			</div>

			<div class=" p-1 h-full flex flex-col gap-2">
				<div class="h-4 animate-pulse rounded-3xl bg-gray-300 w-[90%]" />
				<div class="h-4 animate-pulse rounded-3xl bg-gray-300 w-[50%]" />
				<div class="h-4 animate-pulse rounded-3xl bg-gray-300 w-[30%]" />
				<div class="h-4 animate-pulse rounded-3xl bg-gray-300 w-[50%]" />
				<div class="h-4 animate-pulse rounded-3xl bg-gray-300 w-[64%]" />
				<div class="h-4 animate-pulse rounded-3xl bg-gray-300 w-[80%]" />
				<div class="h-4 animate-pulse rounded-3xl bg-gray-300 w-[30%]" />
				<div class="h-4 animate-pulse rounded-3xl bg-gray-300 w-[64%]" />
				<div class="h-4 animate-pulse rounded-3xl bg-gray-300 w-[70%]" />
				<div class="h-4 animate-pulse rounded-3xl bg-gray-300 w-[50%]" />
				<div class="h-4 animate-pulse rounded-3xl bg-gray-300 w-[64%]" />
				<div class="h-4 animate-pulse rounded-3xl bg-gray-300 w-[80%]" />
				<div class="h-4 animate-pulse rounded-3xl bg-gray-300 w-[30%]" />
			</div>
		</section>
		<section id="preview" class="flex items-center justify-center h-full">
			<slot />
		</section>
	</div>
</section>

<style>
	/* Reset some default styles */

	header {
		background-color: #333;
		color: #fff;
		padding: 10px;
	}

	nav ul {
		list-style: none;
	}

	nav ul li {
		display: inline;
	}

	nav ul li a {
		color: #fff;
		text-decoration: none;
	}

	#preview {
		flex: 1;
		background-color: white;
	}
	#main {
		display: flex;
		flex-wrap: wrap;
		height: 430px;
	}

	#editor {
		flex: 1;
	}
</style>
