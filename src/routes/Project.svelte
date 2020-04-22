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
    #projects {
        width: 100%;
        margin-top: 100px;
        margin-bottom: 200px;
        display: flex;
        flex-direction: row;
        justify-content: center;
        background-color: #cf5587;
        color: #FFF;
        flex-wrap: wrap;
    }
    .projects_container {
        display: flex;
        flex-direction: column;
        margin-left: 20px;
        margin-right: 20px;
    }
    .projects_box {
        width: 250px;
        height: 75px;
        border-bottom: 1px #FFF solid;
        font-size: 30px;
        display: flex;
        justify-content: center;
        align-items: flex-end;
    }
    .projects_box2 {
        width: 250px;
        height: 200px;
        text-align: center;
    }
    @media (max-width: 1000px) {
        #title {
            margin-top: 200px;
            font-size: 150px;
        }
        .projects_container {
            width: 100%;
        }
        .projects_box {
            width: 100%;
            height: 150px;
            border-bottom: 3px #FFF solid;
            font-size: 80px;
        }
        .projects_box2 {
            width: 100%;
            height: 500px;
            font-size: 40px;
            padding-top: 20px;
        }
    }
</style>

<div id="contents">
    <div id="title">
        Project<span class="blink">_</span>
    </div>
    <div id="projects">
        <div class="projects_container">
            <div class="projects_box">
                Haverzard Web 1
            </div>
            <div class="projects_box2">
                My old website created using PUG template.
            </div>
        </div>
        <div class="projects_container">
            <div class="projects_box">
                Coming Soon
            </div>
            <div class="projects_box2">
                May 1st, 2020
            </div>
        </div>
        <div class="projects_container">
            <div class="projects_box">
                Keep the Expense
            </div>
            <div class="projects_box2">
                React Native App for keeping your daily expenses.
            </div>
        </div>
    </div>
</div>