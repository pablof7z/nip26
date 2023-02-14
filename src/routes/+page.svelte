<script>
	import SignEvent from '$lib/sign.svelte';

	let eventSigned = false;
	let content;
	let delegation;
</script>

<svelte:head>
	<title>NIP26.lol</title>
	<meta name="description" content="NIP26.lol" />
</svelte:head>

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
		lg:w-1/2
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

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
	}

	h1 {
		width: 100%;
	}

	.welcome {
		display: block;
		position: relative;
		width: 100%;
		height: 0;
		padding: 0 0 calc(100% * 495 / 2048) 0;
	}

	.welcome img {
		position: absolute;
		width: 100%;
		height: 100%;
		top: 0;
		display: block;
	}
</style>
