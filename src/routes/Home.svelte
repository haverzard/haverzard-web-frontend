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
    #announce {
        width: 100%;
        margin-bottom: 200px;
    }
    .announce_container {
        width: 100%;
        margin-top: 200px;
        display: flex;
        flex-direction: row;
        justify-content: center;
        flex-wrap: wrap;
        background-color: #59608f;
    }
    .announce_box {
        width: 500px;
        height: 500px;
    }
    .announce_title {
        height: 150px;
        font-size: 50px;
        display: flex;
        align-items: flex-end;
        justify-content: center;
        border-bottom: 1px #AAA solid;
    }
    .announce_text {
        text-align: center;
    }
    @media (max-width: 1000px) {
        #title {
            margin-top: 200px;
            font-size: 150px;
        }
        .announce_box {
            width: 100%;
            height: 1000px;
        }
        .announce_title {
            height: 150px;
            font-size: 80px;
            border-bottom: 3px #AAA solid;
        }
        .announce_text {
            font-size: 40px;
        }
    }
</style>

<div id="contents">
    <div id="title">
        haverzard<span class="blink">_</span>
    </div>
    <div id="announce">
        <div class="announce_container">
            <div class="announce_box">
                <img class="announce_box" style="opacity: 0.5;" src="images/main_project.png" alt="Project">              
            </div>
            <div class="announce_box">
                <div class="announce_title">
                    Coming Soon
                </div>
                <div class="announce_text">
                    May 1st, 2020
                </div>
            </div>
        </div>
    </div>
</div>