<script lang="ts">
	import SignEvent from '$lib/sign.svelte';

	let eventSigned = false;
	let content : any;
	let delegation : any;
</script>

<svelte:head>
	<title>NIP26.lol</title>
	<meta name="description" content="NIP26.lol" />
</svelte:head>

<div class="flex flex-col lg:flex-row items-center justify-center gap-4 lg:gap-24 p-5 lg:p-1">
	<div class="flex flex-col items-center min-h-screen justify-center">
		<h1 class="text-7xl my-3 text-black font-black">
			NIP-26 Demo
		</h1>
		
		{#if delegation}
			<h1 class="text-4xl">
				Delegation token 👇
			</h1>
			<code class="
				p-5 m-5 border border-gray-400 shadow-lg
				bg-white
				rounded-lg
				flex flex-col
			">
				<div class="flex flex-row gap-3">
					<b class="w-24">from:</b>
					<span class="w-max">{delegation.from}</span>
				</div>
				<div class="flex flex-row gap-3">
					<b class="w-24">to: </b>
					<span class="w-max">{delegation.to}</span>
				</div>
				<div class="flex flex-row gap-3 whitespace-normal">
					<b class="w-24">cond:</b>
					<span class="w-max">{delegation.cond}</span>
				</div>
				<div class="flex flex-row gap-3">
					<b class="w-24">sig:</b>
					<span class="w-max">{delegation.sig}</span>
				</div>
			</code>

			<div class="max-w-prose text-xl leading-8 my-5 text-center">
				An app using this token can now sign events on your behalf within the conditions
				set by the delegation token (<code>cond</code>).
			</div>

			<button
				on:click={() => { delegation = null}}
				class="
				bg-dark-blue-900 dark:bg-purple-1000
				w-fit
				p-6
				text-white tracking-widest rounded-lg
			">
			<div class="flex flex-row gap-4">
				<span class="font-semibold text-xl">
					Make another one
				</span>
			</div>
		</button>
		{:else}
			<h2 class="text-xl max-w-prose my-3">
				Use your NIP-26-compatible browser extension to generate a delegation token.
			</h2>
			
			<div class="
			w-full
			px-5 md:px-0
		">
				<textarea bind:value={content} name="content" placeholder="Type up your message here" required class="
				w-full
				max-w-5xl
				bg-transparent
				border-gray-700
				resize-none
				rounded-xl md:rounded-3xl
				p-5 lg:p-10x
				border 
				my-10
				" style="box-shadow: 0 0px 30px 0px rgb(147 51 234 / var(--tw-text-opacity)); height: 30vh;"></textarea>
			</div>
				<SignEvent on:signed={()=>{eventSigned=true}} {content} bind:delegation={delegation} />
		{/if}
	</div>

	<div class="text-xl flex flex-col gap-6 lg:w-1/2">
		<div class="flex flex-col gap-2">
			<h2 class="text-2xl text-purple-900 font-black">
				What is NIP-26?
			</h2>

			<div class="text-justify text-slate-500">
				NIP-26 is a standard for signing events on behalf of a user. It allows
				a second set of keys to create events that compatible-clients will
				render as belong to the delegator user.
			</div>
		</div>
		
		<div class="flex flex-col gap-2">
			<h2 class="text-2xl text-purple-900 font-black">
				What clients support NIP-26?
			</h2>

			<ul>
				<div class="flex flex-row items-center gap-2">
					<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-10 h-10 text-purple-500">
						<path fill-rule="evenodd" d="M8.603 3.799A4.49 4.49 0 0112 2.25c1.357 0 2.573.6 3.397 1.549a4.49 4.49 0 013.498 1.307 4.491 4.491 0 011.307 3.497A4.49 4.49 0 0121.75 12a4.49 4.49 0 01-1.549 3.397 4.491 4.491 0 01-1.307 3.497 4.491 4.491 0 01-3.497 1.307A4.49 4.49 0 0112 21.75a4.49 4.49 0 01-3.397-1.549 4.49 4.49 0 01-3.498-1.306 4.491 4.491 0 01-1.307-3.498A4.49 4.49 0 012.25 12c0-1.357.6-2.573 1.549-3.397a4.49 4.49 0 011.307-3.497 4.49 4.49 0 013.497-1.307zm7.007 6.387a.75.75 0 10-1.22-.872l-3.236 4.53L9.53 12.22a.75.75 0 00-1.06 1.06l2.25 2.25a.75.75 0 001.14-.094l3.75-5.25z" clip-rule="evenodd" />
					</svg>
					
					<span class="font-semibold">Snort</span>
				</div>

				<div class="flex flex-row items-center gap-2">
					<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-10 h-10 text-purple-600">
						<path stroke-linecap="round" stroke-linejoin="round" d="M12 6v6h4.5m4.5 0a9 9 0 11-18 0 9 9 0 0118 0z" />
					</svg>
					
					<div class="flex flex-col">
						<span class="font-semibold">
							Damus
						</span>
						<span class="text-sm opacity-70">
							<code>@pablof7z</code> working on it &mdash;
							want to help?
						</span>
					</div>
				</div>
			</ul>
		</div>

		<div class="flex flex-col gap-2">
			<h2 class="text-2xl text-purple-900 font-black">
				What browser extensions support NIP-26?
			</h2>

			<ul>
				<div class="flex flex-row items-center gap-2">
					<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-10 h-10 text-purple-600">
						<path stroke-linecap="round" stroke-linejoin="round" d="M12 6v6h4.5m4.5 0a9 9 0 11-18 0 9 9 0 0118 0z" />
					</svg>
					
					<div class="flex flex-col">
						<span class="font-semibold">
							Get Alby
						</span>
						<span class="text-sm opacity-70">
							PR <a href="https://github.com/getAlby/lightning-browser-extension/pull/2063">#2063</a> waiting to be merged.
						</span>
					</div>
				</div>
			</ul>
		</div>
	</div>
</div>
