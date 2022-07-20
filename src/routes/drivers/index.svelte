<script>
    import { onMount } from 'svelte';
    import { supabase } from '$lib/supabaseClient';
    import { drivers} from '../../stores/drivers.js';

    onMount(async () => {
        const {data} = await supabase
            .from('Drivers')
            .select()
        drivers.set(data)
    });
</script>
<div class="container mx-auto px-4 mt-4">
    <div class="text-sm breadcrumbs">
        <ul>
            <li><a href="/drivers">Drivers</a></li>
        </ul>
    </div>
    <hr/>
    <br/>
    <div class="flex justify-between">
        <h1 class="text-3xl font-bold mb-4">Drivers</h1>
        <a href="/drivers/new" for="my-modal-3" class="btn btn-default"> <b> + </b> &nbsp; Add Driver</a>
    </div>
    <br/>
    <hr/>
    <div class="overflow-x-auto w-full">
        <table class="table w-full">
            <!-- head -->
            <thead>
            <tr>
                <th>Name</th>
                <th>Phone Number</th>
                <th>Car Registration</th>
                <th></th>
            </tr>
            </thead>
            <tbody>
            <!-- row 1 -->
            {#each $drivers as driver}
            <tr class="hover">

                <td>
                    <div class="flex items-center space-x-3">
                        <div class="avatar">
                            <div class="mask mask-squircle w-12 h-12">
                                <img src="https://placeimg.com/80/80/people" alt="Avatar Tailwind CSS Component" />
                            </div>
                        </div>
                        <div>
                            <div class="font-bold">{driver.name}</div>
                        </div>
                    </div>
                </td>
                <td>
                    {driver.phone}
                </td>
                <td>{driver.car_reg}</td>
                <th>
                    <a href="/drivers/{driver.id}" class="btn btn-ghost btn-xs">details</a>
                    {#if driver.status === "Pending Approval"}
                    <button class="btn btn-ghost btn-xs">Approve</button>
                    {/if }
                    {#if driver.status === "Banned"}
                        <button class="btn btn-ghost btn-xs">Approve</button>
                    {/if }
                    {#if driver.status === "Active"}
                        <button class="btn btn-ghost btn-xs">Ban</button>
                    {/if }
                </th>
            </tr>
            {/each}
            </tbody>
            <!-- foot -->
            <tfoot>
            <tr>
                <th>Name</th>
                <th>Phone Number</th>
                <th>Car Registration</th>
                <th></th>
            </tr>
            </tfoot>

        </table>
    </div>
</div>

<!-- Put this part before </body> tag -->
<div class="modal">
    <div class="modal-box relative">
        <label for="my-modal-3" class="btn btn-sm btn-circle absolute right-2 top-2">✕</label>
        <h3 class="text-lg font-bold">Congratulations random Internet user!</h3>
        <p class="py-4">You've been selected for a chance to get one year of subscription to use Wikipedia for free!</p>
    </div>
</div>