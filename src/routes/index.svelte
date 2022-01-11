<script lang="ts">
import { page } from '$app/stores';

	let dirty = false;

	function setDirty() {
		dirty = true;
	}

    $: param = $page.url.searchParams.get("param");
</script>

<h1>Welcome to SvelteKit</h1>

<h3>Steps to reproduce the bug:</h3>
<ul>
    <li>reload the tab</li>
    <li>click "set dirty" button (Dirty will change to "true")</li>
    <li>then click any param link => notice that dirty is reset to false which is already strange</li>
    <li>click again "set dirty" button</li>
    <li>then click any param link => now you will notice that dirty flag is not reset anymore</li>
</ul>

<button on:click={setDirty}>Set Dirty</button>

<p>Dirty: <span class:dirty>{dirty}</span></p>
<p>Param: {param}</p>

<ul>
	<li><a href="?param=1">param 1</a></li>
	<li><a href="?param=2">param 2</a></li>
	<li><a href="?param=3">param 3</a></li>
	<li><a href="?param=4">param 4</a></li>
</ul>

<style>
    span {
        color: green;
    }
    span.dirty {
        color: red;
    }
</style>
