<style>
	#contents {
		width: 100%;
        min-height: 100vh;
        display: flex;
        align-items: center;
        flex-direction: column;
	}
	.blink {
		animation: blink_text 1s infinite;
	}
	@keyframes blink_text{
		0%{     color: #aaa;    }
		49%{    color: #aaa; }
		60%{    color: transparent; }
		99%{    color:transparent;  }
		100%{   color: #aaa;    }
	}
	#title {
        margin-top: 100px;
		font-size: 70px;
		font-family: "Courier New", Courier, monospace;
    }
    #about {
        width: 100%;
        margin-top: 100px;
        margin-bottom: 200px;
        display: flex;
        flex-direction: row;
        justify-content: center;
        background-color: #62dbf0;
        color: #FFF;
        flex-wrap: wrap;
    }
    .about_container {
        display: flex;
        flex-direction: column;
        margin-left: 20px;
        margin-right: 20px;
    }
    .about_box {
        width: 250px;
        height: 75px;
        border-bottom: 1px #FFF solid;
        font-size: 30px;
        display: flex;
        justify-content: center;
        align-items: flex-end;
    }
    .about_box2 {
        width: 250px;
        height: 200px;
        text-align: center;
    }
    @media (max-width: 1000px) {
        #title {
            margin-top: 200px;
            font-size: 150px;
        }
        .about_container {
            width: 100%;
        }
        .about_box {
            width: 100%;
            height: 150px;
            border-bottom: 3px #FFF solid;
            font-size: 80px;
        }
        .about_box2 {
            width: 100%;
            height: 500px;
            font-size: 40px;
            padding-top: 20px;
        }
    }
</style>

<div id="contents">
    <div id="title">
        About<span class="blink">_</span>
    </div>
    <div id="about">
        <div class="about_container">
            <div class="about_box">
                About Myself
            </div>
            <div class="about_box2">
                A college student that's full of curiosity and creativity. He likes to try new things, especially a new framework!
            </div>
        </div>
        <div class="about_container">
            <div class="about_box">
                My Hobbies
            </div>
            <div class="about_box2">
                I love designing and developing website. Sometimes, I joined some CTF competitions with my friends, focusing on Web Exploitation and Cryptography.
            </div>
        </div>
        <div class="about_container">
            <div class="about_box">
                About this web
            </div>
            <div class="about_box2">
                Nothing special about this website. I created this just for fun and practice.
            </div>
        </div>
    </div>
</div>