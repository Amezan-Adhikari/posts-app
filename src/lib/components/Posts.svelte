<!-- component -->
<!-- This is an example component -->


<script>
  //@ts-nocheck
  import { onMount } from "svelte";
    let contents=[];
    const getContent = ()=>{
        fetchUserData().then((data)=>{
            data.forEach((content) => {
                contents=[content,...contents];
            });
        })
        console.log(contents);
    }

    const fetchUserData = async ()=>{
            const response = await fetch("https://server-for-social-media.onrender.com/");
            const data = await response.json();

            return data;
        }
        onMount(()=>{
          getContent();
        })
        
    </script>


<div class="flex flex-col gap-5 my-2 items-center">
{#each contents as content}
    

<!-- component -->

 
  <blockquote class="container flex flex-wrap flex-col bg-white text-gray-700 border-l-8  shadow-lg border-gray-400 px-4 py-3">
    <h1 class="font-bold uppercase">{content.title}</h1>
   {content.message}
    <span class="container flex justify-end text-sm text-indigo-400 font-semibold pt-2 underline ">{content.username}</span>
  </blockquote>
  


{/each}
</div>