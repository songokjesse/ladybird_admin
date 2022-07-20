
<script>
    import { onMount } from 'svelte';
    import {supabase} from '$lib/supabaseClient'
    import { page } from '$app/stores';
    let id = $page.params.id
    export let driver = []

    onMount(async () => {
        let { data, error, status } = await supabase
            .from('Drivers')
            .select(`name,email,phone,ID_Number,car_reg,status`)
            .eq('id', id)
            .single()
        driver = data
    });
</script>
<div class="container mx-auto px-4 mt-4">
    <div class="text-sm breadcrumbs">
        <ul>
            <li><a href="/drivers">Drivers</a></li>
            <li>{driver.name}</li>
        </ul>
    </div>
    <hr/>

    <div class="card w-full bg-base-100 shadow-xl mt-4">
        <div class="card-body">
                <div class="avatar">
                    <div class="mask mask-squircle w-12 h-12">
                        <img src="https://placeimg.com/80/80/people" alt="Avatar Tailwind CSS Component" />
                    </div>
                </div>
            <h2 class="card-title">{driver.name}</h2>
           <table  class="table w-full">
               <tr class="hover">
                   <td>ID Number : </td>
                   <td>{driver.ID_Number}</td>
               </tr>
               <tr class="hover">
                   <td>Email : </td>
                   <td>{driver.email}</td>
               </tr>
               <tr class="hover">
                   <td>Phone : </td>
                   <td>{driver.phone}</td>
               </tr>
               <tr class="hover">
                   <td>Car Registration : </td>
                   <td>{driver.car_reg}</td>
               </tr>
               <tr class="hover">
                   <td>Status : </td>
                   <td>{driver.status}</td>
               </tr>
           </table>
            <div class="card-actions justify-end">
                <button class="btn btn-primary">Edit</button>
            </div>
        </div>
    </div>
</div>