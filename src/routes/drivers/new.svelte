<script>
    import { supabase } from '$lib/supabaseClient';
    import { createForm } from "svelte-forms-lib";
    import { goto } from '$app/navigation';

    const {form, errors, handleChange, handleSubmit} = createForm({
        initialValues: {
        name: "",
        email: "",
        phone: "",
        car_reg: "",
        ID_Number: "",
    },
    validate: async (values) => {
        let key = ""
        let errors = {};
            if (!values.email) {
                errors.email = "Driver Email is Required";
            } else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(values.email)) {
                errors.email = "Invalid email address";
            } else
        if(await verifyIfItExists( key="email",values.email)) {
                errors.email = "Email already exists";
            }
            if (!values.name) {
                errors["name"] = "Driver Name is required";
            }
            if (!values.phone) {
                errors["phone"] = "Phone is required";
            } else if(await verifyIfItExists( key="phone",values.phone)) {
                errors.phone = "Phone already exists";
            }
            if (!values.car_reg) {
                errors["car_reg"] = "Car Registration is required";
            } else if(await verifyIfItExists( key="car_reg",sanitizeCarRegistration(values.car_reg))) {
                errors.car_reg = "Car Registration already exists";
            }
            if (!values.ID_Number) {
                errors["ID_Number"] = "ID Number is required";
            } else if (await verifyIfItExists( key="ID_Number",values.ID_Number)) {
                errors.ID_Number = "ID Number already exists";
            }
            return errors;
        },
        onSubmit:  async values => {
            let errors = {};
            const { data, error } = await supabase
                .from('Drivers')
                .insert([
                    {
                        name: values.name,
                        email: values.email,
                        phone: values.phone,
                        car_reg: sanitizeCarRegistration(values.car_reg),
                        ID_Number: values.ID_Number,
                        status: "PendingApproval"
                    },
                ])
            if(error) {
                return errors.DB_ERROR = error
            }
            return goto('/drivers');

    }
    });
    const verifyIfItExists = async (key,value) => {
        let { data, error } = await supabase
            .from('Drivers')
            .select(key)
            .eq(key, value)
            .single()
        return !!data;
    }

    const sanitizeCarRegistration = (registration) => {
        return registration.replace(/\s+/g, '').toUpperCase()
    }

</script>
<div class="container mx-auto px-4 mt-4">
    <div class="text-sm breadcrumbs">
        <ul>
            <li><a href="/drivers">Drivers</a></li>
            <li>Add Driver</li>
        </ul>
    </div>
    <hr/>
    {#if $errors.DB_ERROR}
        <span class=" alert alert-error" role="alert">Error Adding Driver</span>
    {/if}
    <div class="card w-full shadow-xl">
        <div class="card-body">
            <h2 class="card-title">Driver Information</h2>
            <form on:submit|preventDefault={handleSubmit}>
                    <label class="label">
                        <span class="label-text">Driver Name</span>
                    </label>
                    <input
                            type="text"
                            placeholder="Name"
                            name="name"
                            class="input input-bordered w-full"
                            on:change={handleChange}
                            bind:value={$form.name}
                    />
                    {#if $errors.name}
                        <span class="alert-error" role="alert">{$errors.name}</span>
                    {/if}

                <label class="label">
                    <span class="label-text">Driver Email</span>
                </label>
                <input
                        type="email"
                        placeholder="Email"
                        name="email"
                        class="input input-bordered w-full"
                        on:change={handleChange}
                        bind:value={$form.email}
                />
                {#if $errors.email}
                    <span class="alert-error" role="alert">{$errors.email}</span>
                {/if}
                <label class="label">
                    <span class="label-text">Mobile Phone Number</span>
                </label>
                <input
                        type="text"
                        placeholder="Phone"
                        name="phone"
                        class="input input-bordered w-full"
                        on:change={handleChange}
                        bind:value={$form.phone}
                />
                {#if $errors.phone}
                    <span class="alert-error" role="alert">{$errors.phone}</span>
                {/if}
                <label class="label">
                    <span class="label-text">National ID Number</span>
                </label>
                <input
                        type="text"
                        placeholder="ID Number"
                        name="ID_Number"
                        class="input input-bordered w-full"
                        on:change={handleChange}
                        bind:value={$form.ID_Number}
                />
                {#if $errors.ID_Number}
                    <span class="alert-error" role="alert">{$errors.ID_Number}</span>
                {/if}

                <label class="label">
                    <span class="label-text">Car Registration</span>
                </label>
                <input
                        type="text"
                        placeholder="Car Registration"
                        class="input input-bordered w-full"
                        on:change={handleChange}
                        bind:value={$form.car_reg}
                />
                {#if $errors.car_reg}
                    <span class="alert-error" role="alert">{$errors.car_reg}</span>
                {/if}
                <div class="card-actions justify-end">
                    <br/>
                    <button class="btn btn-primary mt-2">Save</button>
                </div>
            </form>
        </div>
    </div>
</div>