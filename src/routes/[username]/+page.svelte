<script>
	import { HighlightAuto, LineNumbers } from 'svelte-highlight';
	import Nav from '../../components/nav.svelte';
	import { darkModeState } from '$lib/index.js';
	// import { d } from 'svelte-highlight/languages/index.js';
	import { github, githubDark, atomOneDark } from 'svelte-highlight/styles';
	import Fa from 'svelte-fa';
	import { faPen } from '@fortawesome/free-solid-svg-icons';
	import { onMount, setContext } from 'svelte';
	import NavWrapper from '../../components/snips/navWrapper.svelte';
	import { faGithub, faInstagram, faTwitter } from '@fortawesome/free-brands-svg-icons';
	import Collection from '../../components/user/collection.svelte';
	import { pageCountSnips, pageCountPl } from '$lib/index.js';

	export let data;

	onMount(() => {
		pageCountPl.set(12);
		pageCountSnips.set(6);
	});
</script>

<svelte:head>
	{#if data.isFound}
		<title>{data.details.name}</title>

		<!-- Facebook Meta Tags -->
		<!-- <meta property="og:title" content={data['0'].description} />-->

		<!-- Twitter Meta Tags  -->
		<!-- <meta name="twitter:title" content={data['0'].description} /> -->
	{/if}
	<!-- HTML Meta Tags -->

	{#if $darkModeState}
		{@html githubDark}
	{:else}
		{@html github}
	{/if}
</svelte:head>

<article class="h-screen flex flex-col">
	<NavWrapper>
		<main class="flex flex-col items-center h-full p-3">
			<div
				id="userinfo"
				class="flex items-center flex-col gap-3 w-full border-b-2 dark:border-secondary-dark py-2 md:py-4"
			>
				<div class="h-24 w-24 bg-sky-500 rounded-xl" />
				<h1 class="text-3xl capitalize">
					{data.details.name}
				</h1>

				<div class="flex gap-2">
					{#each Object.keys(data.details.socials) as site}
						<!-- {site} -->

						{#if data.details.socials[site]}
							{#if site == 'github'}
								<a href={`https://github.com/${data.details.socials[site]}`} target="_blank"
									><Fa icon={faGithub} /></a
								>
							{/if}
							{#if site == 'twitter'}
								<a href={`https://twitter.com/${data.details.socials[site]}`} target="_blank"
									><Fa icon={faTwitter} /></a
								>
							{/if}
							{#if site == 'instagram'}
								<a href={`https://instagram.com/${data.details.socials[site]}`} target="_blank"
									><Fa icon={faInstagram} /></a
								>
							{/if}
						{/if}
					{/each}
				</div>
			</div>

			<div id="collections" class="w-full">
				<div class="h-full flex flex-col">
					<h2 class="text-2xl py-4">Collections</h2>
					<div class="h-full w-full">
						<!-- <p class="text-3xl">Apologies, In Progess 😋.....</p> -->
						<Collection data={{ supabase: data.supabase, user_id: data.details.user_id }} />
					</div>
				</div>
			</div>
			<!-- {JSON.stringify(data.details.socials)} -->

			<!-- {#key data.details.socials} 
					{}
				{/key} -->
		</main>
	</NavWrapper>
</article>

<style>
	/* Hide the vertical scrollbar */
	::-webkit-scrollbar {
		width: 0;
	}

	/* Hide the horizontal scrollbar */
	::-webkit-scrollbar {
		height: 0;
	}
</style>
