<!DOCTYPE html>
<html>
<head>
<title>Pro Presenter Ultimate+</title>

<style>
body {
    margin: 0;
    font-family: 'Segoe UI', sans-serif;
    background: linear-gradient(135deg, #141e30, #243b55);
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
}

/* MAIN */
#app {
    width: 1600px;
    height: 850px;
    border-radius: 20px;
    display: flex;
    overflow: hidden;
    backdrop-filter: blur(20px);
    box-shadow: 0 20px 50px rgba(0,0,0,0.6);
}

/* LEFT */
#leftPanel {
    width: 30%;
    padding: 20px;
    display: flex;
    flex-direction: column;
    background: rgba(255,255,255,0.05);
}

#inputArea {
    flex: 1;
    padding: 15px;
    font-size: 16px;
    border-radius: 10px;
    border: none;
    outline: none;
    background: rgba(255,255,255,0.08);
    color: white;
}

/* CENTER */
#centerPanel {
    width: 50%;
    display: flex;
    flex-direction: column;
}

#previewPanel {
    height: 25%;
    background: black;
    position: relative;
}

/* SLIDES GRID */
#bottomPanel {
    flex: 1;
    display: grid;
    grid-template-columns: repeat(4,1fr);
    gap: 12px;
    padding: 15px;
    overflow-y: auto;
}

/* RIGHT */
#historyPanel {
    width: 20%;
    padding: 15px;
    overflow-y: auto;
    background: rgba(0,0,0,0.4);
    color: white;
}

/* HISTORY */
.historyItem {
    background: rgba(255,255,255,0.08);
    padding: 10px;
    margin-bottom: 10px;
    cursor: pointer;
    border-radius: 8px;
}

/* SLIDE */
.slide {
    position: absolute;
    width: 100%;
    height: 100%;
    display:flex;
    justify-content:center;
    align-items:flex-end;
    opacity:0;
    transition:0.4s;
}
.slide.active { opacity:1; }

/* TEXT */
.slideText {
    color: white;
    font-size: 28px;
    text-align: center;
    max-width: 85%;
    margin-bottom: 40px;
    line-height: 1.5;
}

/* THUMB */
.slideItem {
    height:120px;
    background: rgba(255,255,255,0.08);
    padding:10px;
    cursor:pointer;
    border-radius:10px;
    color:white;
}
.slideItem.active {
    border:2px solid #00c6ff;
}

/* BUTTON */
button {
    margin-top: 10px;
    padding: 12px;
    border: none;
    background: #00c6ff;
    color: white;
    border-radius: 8px;
    cursor: pointer;
}
</style>
</head>

<body>

<div id="app">

<!-- LEFT -->
<div id="leftPanel">
    <textarea id="inputArea" placeholder="Paste lyrics..."></textarea>
    <button onclick="generateSlides()">Generate</button>
    <button onclick="openOutput()">Open Output</button>
</div>

<!-- CENTER -->
<div id="centerPanel">
    <div id="previewPanel"></div>
    <div id="bottomPanel"></div>
</div>

<!-- RIGHT -->
<div id="historyPanel">
    <h3>Recent Songs</h3>
</div>

</div>

<script>
let slides=[];
let currentIndex=0;
let outputWindow=null;

/* RENDER */
function renderSlides(data){
    let preview=document.getElementById("previewPanel");
    let bottom=document.getElementById("bottomPanel");

    preview.innerHTML="";
    bottom.innerHTML="";

    data.forEach((s,i)=>{
        let slide=document.createElement("div");
        slide.className="slide";

        let text=document.createElement("div");
        text.className="slideText";
        text.innerText=s;

        slide.appendChild(text);
        preview.appendChild(slide);

        let thumb=document.createElement("div");
        thumb.className="slideItem";
        thumb.innerText=s.substring(0,60);
        thumb.onclick=()=>showSlide(i);
        bottom.appendChild(thumb);
    });

    setTimeout(()=>showSlide(0),50);
}

/* GENERATE */
function generateSlides(){
    let text=document.getElementById("inputArea").value.trim();
    if(!text) return;

    slides = text.split(/\n\s*\n/).filter(s=>s);

    let history = JSON.parse(localStorage.getItem("history") || "[]");
    history = history.filter(item => item.text !== text);
    history.unshift({ text, slides });

    localStorage.setItem("history", JSON.stringify(history));

    renderSlides(slides);
    loadHistory();
}

/* HISTORY */
function loadHistory(){
    let panel=document.getElementById("historyPanel");
    panel.innerHTML="<h3>Recent Songs</h3>";

    let history=JSON.parse(localStorage.getItem("history")||"[]");

    history.forEach(item=>{
        let div=document.createElement("div");
        div.className="historyItem";
        div.innerText=item.text.substring(0,50);

        div.onclick=()=>{
            document.getElementById("inputArea").value=item.text;
            slides=item.slides;
            renderSlides(slides);
        };

        panel.appendChild(div);
    });
}

/* SHOW */
function showSlide(i){
    if(i<0 || i>=slides.length) return;

    currentIndex=i;

    document.querySelectorAll(".slide").forEach((s,idx)=>{
        s.classList.toggle("active",idx===i);
    });

    document.querySelectorAll(".slideItem").forEach((s,idx)=>{
        s.classList.toggle("active",idx===i);
    });

    if(outputWindow && !outputWindow.closed){
        outputWindow.postMessage({slide:slides[i]},"*");
    }
}

/* OUTPUT FINAL POSITION */
function openOutput(){
    let width = screen.availWidth;
    let height = screen.availHeight;

    outputWindow = window.open("", "_blank",
        `width=${width},height=${height},top=0,left=0`);

    outputWindow.document.open();
    outputWindow.document.write(`
        <html>
        <body style="
            margin:0;
            background:black;
            color:white;
            font-size:60px;
            display:flex;
            justify-content:center;
            align-items:flex-end;
            height:100vh;
            text-align:center;
            overflow:hidden;
            padding-bottom:240px;
        ">
        <div id="slide" style="max-width:90%; line-height:1.4;"></div>

        <script>
        window.addEventListener("message",e=>{
            document.getElementById("slide").innerText=e.data.slide;
        });
        <\/script>
        </body>
        </html>
    `);
    outputWindow.document.close();

    setTimeout(()=>{
        if(slides.length > 0){
            outputWindow.postMessage({slide:slides[0]},"*");
        }
    },300);
}

/* KEYBOARD */
document.addEventListener("keydown", e=>{
    if(e.key==="ArrowRight") showSlide(currentIndex+1);
    if(e.key==="ArrowLeft") showSlide(currentIndex-1);
});

/* INIT */
loadHistory();
</script>

</body>
</html>