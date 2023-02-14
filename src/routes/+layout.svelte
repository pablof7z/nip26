<script>
	import './styles.css';
</script>

<div class="app">
	<main class="max-w-6xl m-auto mb-24">
		<slot />
	</main>

	<footer class="
		fixed
		bottom-0
		w-full
		bg-slate-900
		text-white
	">
		<p>
			Proof of NIP by
			<a href="https://pablof7z.com">@pablof7z</a>
		</p>
	</footer>

	<div class="hidden md:block">
		<script
			src="https://nostri.chat/public/bundle.js"
			data-website-owner-pubkey="fa984bd7dbb282f07e16e7ae87b26a2a7b9b90b7246a44771f0cf5ae58018f52"
			data-chat-type="GLOBAL" 
			data-chat-tags="#nip26"
			data-relays="wss://relay.f7z.io,wss://nos.lol,wss://relay.nostr.info,wss://nostr-pub.wellorder.net,wss://relay.current.fyi,wss://relay.nostr.band"
		></script>
		<link rel="stylesheet" href="https://nostri.chat/public/bundle.css" />
	</div>
</div>

<style>
	footer {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		padding: 12px;
	}

	footer a {
		font-weight: bold;
	}

	@tailwind base;
	@tailwind components;
	@tailwind utilities;
</style>