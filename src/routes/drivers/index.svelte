
<div class="container mx-auto px-4 mt-4">
    <br/>
    <div class="flex justify-between">
        <h1 class="text-3xl font-bold mb-4">Drivers</h1>
        <a href="/drivers/new" for="my-modal-3" class="btn btn-default"> <b> + </b> &nbsp; Add Driver</a>
    </div>
    <hr/>
    <div class="overflow-x-auto w-full">
        <table class="table w-full">
            <!-- head -->
            <thead>
            <tr>
                <th>
                    <label>
                        <input type="checkbox" class="checkbox" />
                    </label>
                </th>
                <th>Name</th>
                <th>Job</th>
                <th>Favorite Color</th>
                <th></th>
            </tr>
            </thead>
            <tbody>
            <!-- row 1 -->
            <tr>
                <th>
                    <label>
                        <input type="checkbox" class="checkbox" />
                    </label>
                </th>
                <td>
                    <div class="flex items-center space-x-3">
                        <div class="avatar">
                            <div class="mask mask-squircle w-12 h-12">
                                <img src="/tailwind-css-component-profile-2@56w.png" alt="Avatar Tailwind CSS Component" />
                            </div>
                        </div>
                        <div>
                            <div class="font-bold">Hart Hagerty</div>
                            <div class="text-sm opacity-50">United States</div>
                        </div>
                    </div>
                </td>
                <td>
                    Zemlak, Daniel and Leannon
                    <br>
                    <span class="badge badge-ghost badge-sm">Desktop Support Technician</span>
                </td>
                <td>Purple</td>
                <th>
                    <button class="btn btn-ghost btn-xs">details</button>
                </th>
            </tr>
            <!-- row 2 -->
            <tr>
                <th>
                    <label>
                        <input type="checkbox" class="checkbox" />
                    </label>
                </th>
                <td>
                    <div class="flex items-center space-x-3">
                        <div class="avatar">
                            <div class="mask mask-squircle w-12 h-12">
                                <img src="/tailwind-css-component-profile-3@56w.png" alt="Avatar Tailwind CSS Component" />
                            </div>
                        </div>
                        <div>
                            <div class="font-bold">Brice Swyre</div>
                            <div class="text-sm opacity-50">China</div>
                        </div>
                    </div>
                </td>
                <td>
                    Carroll Group
                    <br>
                    <span class="badge badge-ghost badge-sm">Tax Accountant</span>
                </td>
                <td>Red</td>
                <th>
                    <button class="btn btn-ghost btn-xs">details</button>
                </th>
            </tr>
            <!-- row 3 -->
            <tr>
                <th>
                    <label>
                        <input type="checkbox" class="checkbox" />
                    </label>
                </th>
                <td>
                    <div class="flex items-center space-x-3">
                        <div class="avatar">
                            <div class="mask mask-squircle w-12 h-12">
                                <img src="/tailwind-css-component-profile-4@56w.png" alt="Avatar Tailwind CSS Component" />
                            </div>
                        </div>
                        <div>
                            <div class="font-bold">Marjy Ferencz</div>
                            <div class="text-sm opacity-50">Russia</div>
                        </div>
                    </div>
                </td>
                <td>
                    Rowe-Schoen
                    <br>
                    <span class="badge badge-ghost badge-sm">Office Assistant I</span>
                </td>
                <td>Crimson</td>
                <th>
                    <button class="btn btn-ghost btn-xs">details</button>
                </th>
            </tr>
            <!-- row 4 -->
            <tr>
                <th>
                    <label>
                        <input type="checkbox" class="checkbox" />
                    </label>
                </th>
                <td>
                    <div class="flex items-center space-x-3">
                        <div class="avatar">
                            <div class="mask mask-squircle w-12 h-12">
                                <img src="/tailwind-css-component-profile-5@56w.png" alt="Avatar Tailwind CSS Component" />
                            </div>
                        </div>
                        <div>
                            <div class="font-bold">Yancy Tear</div>
                            <div class="text-sm opacity-50">Brazil</div>
                        </div>
                    </div>
                </td>
                <td>
                    Wyman-Ledner
                    <br>
                    <span class="badge badge-ghost badge-sm">Community Outreach Specialist</span>
                </td>
                <td>Indigo</td>
                <th>
                    <button class="btn btn-ghost btn-xs">details</button>
                </th>
            </tr>
            </tbody>
            <!-- foot -->
            <tfoot>
            <tr>
                <th></th>
                <th>Name</th>
                <th>Job</th>
                <th>Favorite Color</th>
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