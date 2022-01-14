<script>
  export let posts;
</script>

<script context="module">
	/** @type {import('@sveltejs/kit').Load} */
	export async function load({ params, fetch, session, stuff }) {
		const url = `https://api.reddit.com/r/${params.name}.json`;
		const res = await fetch(url);

		if (res.ok) {
			return {
				props: {
					posts: (await res.json()).data.children
				}
			};
		}

		return {
			status: res.status,
			error: new Error(`Could not load ${url}`)
		};
	}
</script>

{#each posts as post}
  <div class="post">
    <h4>
      <a
        target="_blank"
        rel="noopener noreferrer"
        href={`https://www.reddit.com${post.data.permalink}`}>
          {post.data.title}
      </a>
      {#if post.data.secure_media}
        {#if post.data.secure_media.reddit_video}
          <video muted autoplay loop src={post.data.secure_media.reddit_video.fallback_url}></video>
        {/if}
      {:else if post.data.post_hint === 'image'}
        <img alt={post.data.title} src={post.data.url}>
      {/if}
    </h4>
  </div>
{/each}

<style>
.post {
  outline: 2px solid white;
  padding: 2rem;
  margin: 1rem;
}

video, img {
  width: 100%;
}
</style>