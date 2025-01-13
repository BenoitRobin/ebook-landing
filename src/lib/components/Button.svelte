<script>
    let { children, ...props } = $props();
    import { loadStripe } from '@stripe/stripe-js';
    import { PUBLIC_STRIPE_KEY } from '$env/static/public'


    async function onclick() {
        const stripe = await loadStripe(PUBLIC_STRIPE_KEY);

        const response = await fetch('api/checkout', {
            method: "POST",
            headers: {
                "Content-Type": "application/json"
            }
        })
        const {sessionId} = await response.json();

        await stripe.redirectToCheckout({sessionId});
    }
</script>

<button {...props} {onclick}>{@render children()}</button>


<style>
    button {
        background-color: #000;
        color: #fff;
        padding: 20px 24px;
        font-weight: normal;
        font-size: 22px;
        text-transform: uppercase;
        border: 1px solid #fff;
        transition: all .3s;
    }

    button:hover {
        background-color: #fff;
        color: #000;
    }
</style>