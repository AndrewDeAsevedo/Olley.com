<script>
  import { createEventDispatcher } from 'svelte';

  let postContent = '';
  const dispatch = createEventDispatcher();

  const createPost = () => {
      console.log('CreatePost function called'); // Debugging log
      if (postContent.trim()) {
          console.log('Post content:', postContent); // Log post content
          dispatch('createPost', postContent); // Send the new post content back to the parent
          postContent = ''; // Clear the input after submitting
      } else {
          console.log('Post content is empty'); // Log if post content is empty
      }
  };
</script>

<div class="bg-white shadow-md rounded-lg p-4 mb-4">
  <h2 class="text-lg font-semibold mb-3">Create a Post</h2>
  <textarea bind:value={postContent} rows="4" class="w-full p-2 border rounded" placeholder="What's on your mind?"></textarea>
  <button on:click={createPost} class="bg-blue-500 text-white px-4 py-2 mt-2 rounded hover:bg-blue-700">Post</button>
</div>
