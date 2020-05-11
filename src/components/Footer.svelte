<script>
	import { fly } from 'svelte/transition'
	let lock = false
	let visible = true
	function goInstagram() {
		location.assign('https://www.instagram.com/haverzard/')
	}
	function goGithub() {
		location.assign('https://github.com/haverzard')
	}
	function goGmail() {
		if (!lock && visible) {
			lock = true
			var dummy = document.createElement("textarea")
			document.body.appendChild(dummy)
			dummy.value = "yonatanviody@gmail.com"
			dummy.select()
			document.execCommand("Copy")
			document.body.removeChild(dummy)
			document.getElementsByClassName('copy_text')[0].style.display = "block"
			visible = false
		}
	}
</script>
<style>
	#footer {
		width: 100%;
		min-height: 10vh;
		background-color: #253770;
		color: #FFF;
		padding-top: 20px;
		display: flex;
		flex-direction: column;
		align-items: center;
		font-family: 'Courier New', Courier, monospace;
	}
	#social_media {
		display: flex;
		flex-direction: row;
		padding-top: 30px;
		padding-bottom: 30px;
	}
	.social_media_img {
		width: 30px;
		height: 30px;
		margin-left: 15px;
		margin-right: 15px;
	}
	.social_media_img2 {
		width: 30px;
		height: 30px;
		cursor: pointer;
	}
	.copy_text {
		position: absolute; 
		display: none;
	}
    @media (max-width: 1000px) {
		#footer {
			padding-top: 100px;
			font-size: 40px;
		}
		#social_media {
			padding-top: 60px;
			padding-bottom: 60px;
		}
		.social_media_img {
			width: 100px;
			height: 100px;
			margin-left: 30px;
			margin-right: 30px;
		}
		.social_media_img2 {
			width: 100px;
			height: 100px;
		}
	}
</style>

<div id="footer">
    <div>
        Created and designed by haverzard.	
    </div>
    <div id="social_media">
        <a href="https://www.instagram.com/haverzard/"><img class="social_media_img" src="images/instagram.png" alt="instagram"></a>
         <a href="https://github.com/haverzard"><img on:click={goGithub} class="social_media_img" src="images/github.png" alt="github"></a>
        <div class="social_media_img">
			<img class="social_media_img2" style="position:absolute" on:click={goGmail} src="images/gmail.png" alt="gmail">
			
			{#if visible}
				<p class="copy_text" 
					transition:fly="{{ y: -50, duration: 500 }}"
					on:introend={()=>lock = false }
					on:outroend={()=>visible = true}>
					Copied
				</p>
			{/if}
		</div>
    </div>
</div>