<!-- component -->
<script>

    let profileDropdownMenu = false;
    let profileSideBarMenu = false;
 
</script>

<link rel="stylesheet" href="https://unpkg.com/boxicons@2.0.7/css/boxicons.min.css" />

<!-- page -->
<main class="min-h-screen w-full bg-gray-100 text-gray-700">
    <!-- header page -->
    <header class="flex w-full items-center sticky top-0 justify-between border-b-2 border-gray-200 bg-white p-2 h-16">
        <!-- logo -->
        <div class="flex items-center space-x-2">
            <button type="button" class="text-3xl" on:click={()=>{profileSideBarMenu = ! profileSideBarMenu}}><i class="bx bx-menu"></i></button>
            <div></div>
        </div>
        <a href="/posts/addpost"><div class="flex items-center bg-blue-500 p-2 px-4 font-bold rounded-lg cursor-pointer text-white gap-4">
            <i class="bx bx-plus"></i>
        </div></a>

        <!-- button profile -->
        <div>
            <button type="button" 
                class="h-6 w-6 overflow-hidden border p-1 border-gray-400 mr-4 rounded-full" on:click={()=>{profileDropdownMenu = ! profileDropdownMenu}}>
                <img src="/images/profile.png" alt="profile"/>
            </button>

            <!-- dropdown profile -->
            <div class="absolute right-2 mt-1 w-48 {profileDropdownMenu === true ? "visible" : "hidden"} divide-y divide-gray-200 rounded-md border border-gray-200 bg-white shadow-md"
                >
                <div class="flex items-center space-x-2 p-2">
                    <img src="/images/profile.png" alt="profile" class="h-6 w-6 border p-1 border-gray-400 rounded-full" />
                    <div class="font-medium">USER</div>
                </div>

                <div class="flex flex-col space-y-3 p-2">
                    <a href="/posts" class="transition hover:text-blue-600">My Profile</a>
                    <a href="/posts" class="transition hover:text-blue-600">Edit Profile</a>
                    <a href="/posts" class="transition hover:text-blue-600">Settings</a>
                </div>

                <div class="p-2">
                    <button class="flex items-center space-x-2 transition hover:text-blue-600" on:click={()=>{
                        window.location.href = "/";
                        
                        }}>
                        <svg class="h-4 w-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"
                            xmlns="http://www.w3.org/2000/svg">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                d="M17 16l4-4m0 0l-4-4m4 4H7m6 4v1a3 3 0 01-3 3H6a3 3 0 01-3-3V7a3 3 0 013-3h4a3 3 0 013 3v1">
                            </path>
                        </svg>
                        <div>Log Out</div>
                    </button>
                </div>
            </div>
        </div>
    </header>

    <div class="flex ">
        <!-- aside -->
        <aside class="flex {profileSideBarMenu === true ? "visible" : "hidden"} w-72 flex-col sticky top-16 space-y-2 border-r-2 border-gray-200 bg-white p-2" style="height: 91vh"
            >
            <a href="/posts" on:click={()=>profileSideBarMenu = !profileSideBarMenu} class="flex items-center space-x-1 rounded-md px-2 py-3 hover:bg-gray-100 hover:text-blue-600">
                <span class="text-2xl"><i class="bx bx-home"></i></span>
                <span>Dashboard</span>
            </a>

            <a href="/posts/addpost" on:click={()=>profileSideBarMenu = !profileSideBarMenu} class="flex items-center space-x-1 rounded-md px-2 py-3 hover:bg-gray-100 hover:text-blue-600">
                <span class="text-2xl"><i class="bx bx-plus"></i></span>
                <span>Add Post</span>
            </a>

            <a href="/posts" on:click={()=>profileSideBarMenu = !profileSideBarMenu} class="flex items-center space-x-1 rounded-md px-2 py-3 hover:bg-gray-100 hover:text-blue-600">
                <span class="text-2xl"><i class="bx bx-user"></i></span>
                <span>Profile</span>
            </a>
        </aside>

        <!-- main content page -->
        <div class="w-full p-4"><slot></slot></div>
    </div>
</main>
