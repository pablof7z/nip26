<script>
    import { generatePrivateKey, getPublicKey, getEventHash, signEvent, relayInit } from 'nostr-tools';
    import {utf8Encoder} from 'nostr-tools/utils'
    import * as secp256k1 from '@noble/secp256k1'
    import {sha256} from '@noble/hashes/sha256'

    export let content;
    export let delegation;

    async function signWithBrowser() {
        let signer;

        const sk = '77e3047bd017adc9774c45a98297a121a69091003545564ff9b95d6f65aa391e';
        const pk = getPublicKey(sk);
        // const sk = generatePrivateKey();
        // const pk = getPublicKey(sk);

        if (!window.nostr?.nip26) {
            alert('Nostr with nip26 extension not found');
            return;
        }
        
        const {from, to, cond, sig} = await window.nostr.nip26.delegate(
            pk,
            {
                kind: 1,
                content
            },
        );

        delegation = {from, to, cond, sig};
        // console.log({from, to, cond, sig});

        // let event = {
        //     kind: 1,
        //     created_at: Math.floor(Date.now() / 1000),
        //     pubkey: pk,
        //     content,
        //     tags: [
        //         [
        //             'delegation',
        //             from,
        //             cond,
        //             sig
        //         ]
        //     ]
        // }
        // event.id = getEventHash(event)

        // console.log({id: event.id});
        
        // event.sig = signEvent(event, sk);

        // const relay = relayInit('wss://nos.lol')
        // await relay.connect()
        // relay.on('connect', () => {
        // console.log(`connected to ${relay.url}`)
        // })
        // relay.on('error', () => {
        // console.log(`failed to connect to ${relay.url}`)
        // })
        // let pub = relay.publish(event)
        // pub.on('ok', () => {
        // console.log(`${relay.url} has accepted our event`)
        // })
        // pub.on('seen', () => {
        // console.log(`we saw the event on ${relay.url}`)
        // })
        // pub.on('failed', reason => {
        // console.log(`failed to publish to ${relay.url}: ${reason}`)
        // })
    }

    // try {
    //     window.nostr.getPublicKey().then(async (pubkey) => {
    //         // signer = new NstrAdapterExtension(pubkey);

    //         let event = createPayload();
    //         // event.pubkey = pubkey;
    //         event = await signer.signEvent(event);
    //         // event.sig = await signer.signEvent(event);
    //         console.log('signed', event);
    //     });
    // } catch (e) {
    //     console.log(e);
    // }
</script>

<div class="flex items-center justify-center">
    <button
        on:click={signWithBrowser}
        class="
        bg-dark-blue-900 dark:bg-purple-1000
        w-fit
        p-6
        text-white tracking-widest rounded-lg
        ">
        <div class="flex flex-row gap-4">
            <span class="font-semibold text-xl">
                Generate delegation token
            </span>
        </div>
    </button>
</div>

<style>
	@tailwind base;
	@tailwind components;
	@tailwind utilities;
</style>