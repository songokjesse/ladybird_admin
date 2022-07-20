<script>
    let name
    let email
    let phone
    let car_reg
    const handleSubmit = () => {
        $: console.log('Form submited')
    }
</script>
<div class="container mx-auto px-4 mt-4">
    <div class="card w-full shadow-xl">
        <div class="card-body">
            <h2 class="card-title">Driver Information</h2>
            <form on:submit|preventDefault={handleSubmit}>
                    <label class="label">
                        <span class="label-text">What is your name?</span>
                    </label>
                    <input type="text" placeholder="Name" class="input input-bordered w-full"  bind:value={name}/>

                <label class="label">
                    <span class="label-text">Email</span>
                </label>
                <input type="email" placeholder="Email" class="input input-bordered w-full" bind:value={email} />

                <label class="label">
                    <span class="label-text">Mobile Phone Number</span>
                </label>
                <input type="text" placeholder="Phone" class="input input-bordered w-full" bind:value={phone}/>

                <label class="label">
                    <span class="label-text">Car Registration</span>
                </label>
                <input type="text" placeholder="Car Registration" class="input input-bordered w-full" bind:value={car_reg}/>
                <div class="card-actions justify-end">
                    <button class="btn btn-primary mt-2">Save</button>
                </div>
            </form>
        </div>
    </div>
</div>