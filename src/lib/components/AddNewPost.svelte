<form>
    <div class="bg-indigo-50 min-h-screen md:px-20 pt-6">
      <div class=" bg-white rounded-md px-6 py-10 max-w-2xl mx-auto">
        <h1 class="text-center text-2xl font-bold text-gray-500 mb-10">ADD POST</h1>
        <div class="space-y-4">
          <div>
            <label for="title" class="text-lx font-serif">Title:</label>
            <input type="text" placeholder="title" id="title" class="ml-2 outline-none py-1 px-2 text-md border-2 rounded-md" bind:value={title}/>
          </div>
          <div>
            <label for="description" class="block mb-2 text-lg font-serif">Description:</label>
            <textarea id="description" cols="30" rows="10" placeholder="add your description..." class="w-full font-serif  p-4 text-gray-600 bg-indigo-50 outline-none rounded-md" bind:value={message}></textarea>
          </div>
          <button class=" px-6 py-2 mx-auto block rounded-md text-lg font-semibold text-indigo-100 bg-indigo-600" on:click={postNewContent}>ADD POST</button>
        </div>
      </div>
    </div>
  </form>

  <script>
    //@ts-nocheck
    let title="";
    let message="";
    const postNewContent = ()=>{
      let newPost = {
        "username":`${JSON.parse(localStorage.getItem("userdata")).username}`,
        "title":title,
        "message":message
      }
      senddata(newPost).then((data)=>{
        console.log(data);
        window.location.href = '/posts'
      })
    }

    const senddata = async(newPost)=>{
      const response = await fetch("https://server-for-social-media.onrender.com/addnewpost",{
        method:"POST",
        headers:{
          "Content-Type":"application/json"
        },
        body : JSON.stringify(newPost)
      })
     const data = response.json()

     return data;
    }
  </script>