<script>
    let msg = {
        "now": "??? is coming soon! It's on progress. Please kindly wait",
        "later": "It's not just fast, it's secure and easy to use.",
        "button": "Please Wait!"
    }
</script>

<style>
	#contents {
		width: 100%;
        min-height: 100vh;
        display: flex;
        align-items: center;
        flex-direction: column;
	}
	.blink {
		animation: blink_text 0.7s infinite alternate;
	}
	@keyframes blink_text{
		0%{     color: #000;    }
		100%{    color:transparent;  }
	}
	#title {
        margin-top: 100px;
		font-size: 70px;
		font-family: "Courier New", Courier, monospace;
    }
    #announce {
        width: 100%;
        margin-top: 50px;
        margin-bottom: 200px;
        background-color: #eee;
    }
    .announce_container {
        width: 100%;
        display: flex;
        flex-direction: row;
        justify-content: center;
        flex-wrap: wrap;
    }
    .announce_box {
        width: 1000px;
        height: 500px;
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    .announce_title {
        height: 200px;
        font-size: 50px;
        padding-top: 100px;
        display: flex;
        text-align: center;
    }
    .announce_title::before {
        content: open-quote;
    }
    .announce_title::after {
        content: close-quote;
    }
    .announce_text {
        width: 33%;
        height: 50px;
        font-size: 30px;
        display: flex;
        justify-content: center;
        align-items: center;
        text-align: center;
        border: 3px #1b3c70 solid;
        background-color: #1b3c70;
        color: #fff;
    }
    .announce_text:hover {
        background-color: #70a7ff;
        border: 3px #387ce8 solid;
        color: #eee;
    }
    @media (max-width: 1000px) {
        #title {
            margin-top: 200px;
            font-size: 150px;
        }
        .announce_box {
            width: 88%;
            height: 1000px;
        }
        .announce_title {
            margin-top: 100px;
            height: 500px;
            font-size: 80px;
        }
        .announce_text {
            height: 100px;
            width: 50%;
            font-size: 60px;
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
                <div class="announce_title">
                    {msg["now"]}
                </div>
                <div class="announce_text">
                    {msg['button']}
                </div>
            </div>
        </div>
    </div>
</div>