<style lang="scss">
	article{
		max-width:600px;
	}
	h1{
		font-size:2em;
		border: 5px solid black;
	}
	p{
		font-size:1.50em;
	}
	img{
		display:block;
		width:100%;
	}
</style>
<script>
	const blogs = (async () => {
		const response = await fetch('https://p0l.herokuapp.com/get?db=blog&limit=2')
    	return await response.json()
	})()
</script>

{#await blogs}
<p>...waiting</p>
{:then data}
<article dir="rtl">
	{#each data as post}
		<h1>{post.title}</h1>
		<img src={post.img} alt="DOG"/>
		<p>{post.body}</p>
	{/each}
</article>
{:catch error}
	<p>An error occurred!</p>
{/await}
