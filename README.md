# Neural-Recuters
file:///C:/Users/smile/Desktop/attendance-calculator%20code.html
<!DOCTYPE html>
<html lang="en"><head><meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<meta name="description" content="BunkBudget: plan your attendance with real SRM Trichy timetables. See what to attend, what you can skip, and get an early detention warning."><meta name="theme-color" content="#2f3cff">
<title>Bunk Budget – Attendance Planner for SRM Trichy</title>
<link rel="preconnect" href="https://fonts.googleapis.com"><link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Bricolage+Grotesque:wght@600;800&family=DM+Sans:wght@400;600&display=swap" rel="stylesheet">
<style>
:root{box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px);
--bg:#eef0ff;--card:#fff;--tx:#14163a;--mu:#5d6190;--bd:#d5d9f5;--blue:#2f3cff;--gold:#ffc933;--coral:#ff4b3e;--mint:#12b886;--skip:#c9cdf0}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#0f1130;--card:#191c47;--tx:#eceeff;--mu:#a3a8dd;--bd:#2f3470;--blue:#7f88ff;--skip:#3a3f80}}
:root[data-theme="dark"]{--bg:#0f1130;--card:#191c47;--tx:#eceeff;--mu:#a3a8dd;--bd:#2f3470;--blue:#7f88ff;--skip:#3a3f80}
html{scroll-padding-top:env(safe-area-inset-top,0px)}*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--tx);font:16px/1.55 "DM Sans",system-ui,sans-serif}
main{max-width:980px;margin:0 auto;padding:20px 16px 48px}
h1,h3,.big{font-family:"Bricolage Grotesque","DM Sans",system-ui,sans-serif}
h1{font-size:clamp(34px,7vw,64px);line-height:1;margin:18px 0 12px;font-weight:800;letter-spacing:-.03em;max-width:14ch}
.lead{color:var(--mu);max-width:52ch;margin:0 0 22px}
.hero{display:grid;grid-template-columns:1fr auto;gap:20px;align-items:end}
.demo{display:grid;grid-template-columns:repeat(6,16px);gap:5px;padding-bottom:10px}
.demo i{width:16px;height:16px;border-radius:4px;background:var(--blue)}.demo i:nth-child(n+4){background:transparent;border:2px solid var(--skip)}.demo i:nth-child(n+7):nth-child(-n+9){background:var(--gold);border:0}
@media(max-width:560px){.demo{display:none}.hero{grid-template-columns:1fr}}
.panel{background:var(--card);border:2px solid var(--tx);border-radius:22px 22px 22px 6px;padding:20px;box-shadow:6px 6px 0 var(--blue)}
.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(180px,1fr));gap:14px}
label{display:block;font-size:13px;font-weight:600;color:var(--mu);margin-bottom:5px}
input,select,textarea{width:100%;padding:11px 12px;border:2px solid var(--bd);border-radius:10px;background:var(--bg);color:var(--tx);font:inherit}
input:focus,select:focus,textarea:focus,button:focus-visible,summary:focus-visible{outline:3px solid var(--gold);outline-offset:2px}
.subj{display:grid;grid-template-columns:1fr 120px;gap:12px;margin-top:12px}
details summary{cursor:pointer;font-weight:600;color:var(--blue);margin-top:14px}
button{margin-top:16px;width:100%;background:var(--tx);color:var(--bg);border:0;border-radius:12px;padding:15px;font:800 18px "Bricolage Grotesque",sans-serif;cursor:pointer;transition:transform .12s}
button:active{transform:scale(.98)}
.alert{margin:26px 0 0;background:var(--coral);color:#fff;border-radius:18px;padding:20px 22px;animation:shake .5s 1}
.alert .big{font-size:clamp(24px,5vw,38px);font-weight:800;display:block;line-height:1.05;margin-bottom:6px}
@keyframes shake{20%{transform:translateX(-8px)}40%{transform:translateX(8px)}60%{transform:translateX(-5px)}80%{transform:translateX(5px)}}
.stats{display:grid;grid-template-columns:repeat(auto-fit,minmax(190px,1fr));gap:12px;margin:24px 0}
.stat{border-left:5px solid var(--blue);padding:2px 0 2px 14px}.stat b{font:800 40px/1 "Bricolage Grotesque",sans-serif;display:block}.stat span{color:var(--mu);font-size:14px}
.legend{display:flex;flex-wrap:wrap;gap:16px;font-size:14px;color:var(--mu);margin-bottom:14px}
.legend i,.t{display:inline-block;width:14px;height:14px;border-radius:4px;vertical-align:-2px;margin-right:6px}
.cards{display:grid;grid-template-columns:repeat(auto-fit,minmax(min(100%,420px),1fr));gap:16px}
.sc{background:var(--card);border:2px solid var(--bd);border-radius:18px;padding:18px}
.sc.bad{border-color:var(--coral)}.sc.ok{border-color:var(--mint)}
.sc header{display:flex;justify-content:space-between;gap:12px;align-items:start}
.sc h3{margin:0;font-size:19px;line-height:1.2}
.pct{font:800 32px/1 "Bricolage Grotesque",sans-serif;text-align:right}.pct small{display:block;font:400 12px "DM Sans";color:var(--mu)}
.strip{display:flex;flex-wrap:wrap;gap:4px;margin:14px 0}
.t{margin:0;background:var(--blue);animation:pop .3s backwards;animation-delay:calc(var(--i)*12ms)}
.t.g{background:var(--gold)}.t.s{background:transparent;border:2px solid var(--skip)}.t.x{background:repeating-linear-gradient(45deg,var(--coral) 0 3px,transparent 3px 6px);border:2px solid var(--coral)}
@keyframes pop{from{transform:scale(0);opacity:0}}
.facts{list-style:none;margin:0;padding:0;font-size:14px}.facts li{padding:6px 0;border-top:1px solid var(--bd)}
.facts b{font-weight:600}
.tag{font-weight:800}.tag.r{color:var(--coral)}.tag.gr{color:var(--mint)}
.note{color:var(--mu);font-size:13px;margin-top:26px}
.top{display:flex;justify-content:space-between;align-items:center;font:800 18px "Bricolage Grotesque",sans-serif;padding-bottom:6px}.top span{font:400 13px "DM Sans";color:var(--mu)}
.chip{display:inline-block;margin-left:8px;font:600 11px "DM Sans";padding:2px 8px;border-radius:99px;border:1.5px solid var(--bd);vertical-align:3px;color:var(--mu)}
.wi{margin:0 0 22px}.wi h3{margin:0 0 4px;font-size:22px}.wi input[type=range]{padding:0;border:0;accent-color:var(--blue)}
.row{display:grid;grid-template-columns:minmax(120px,1.2fr) 2fr 70px;gap:12px;align-items:center;margin-top:10px;font-size:14px}
.bar{height:10px;background:var(--skip);border-radius:6px;position:relative}.bar i{display:block;height:100%;border-radius:6px}.bar b{position:absolute;top:-4px;bottom:-4px;width:2px;background:var(--tx)}
.ghost{background:transparent;color:var(--tx);border:2px solid var(--tx);margin:0 0 20px;font-size:15px;padding:11px}
.prog{height:8px;background:var(--skip);border-radius:6px;margin:6px 0 0}.prog i{display:block;height:100%;background:var(--blue);border-radius:6px}
@media(max-width:560px){.row{grid-template-columns:1fr 60px}.row .bar{grid-column:1/3;order:3}}
.two{display:grid;grid-template-columns:repeat(auto-fit,minmax(min(100%,380px),1fr));gap:16px;margin-bottom:22px}
.leg2{display:flex;gap:12px;flex-wrap:wrap;font-size:13px;color:var(--mu);margin-top:8px}
.lrow{display:flex;justify-content:space-between;align-items:center;gap:8px;padding:6px 10px;border:1.5px solid var(--bd);border-radius:10px;margin-top:8px;font-size:14px}
.lrow button{width:auto;margin:0;padding:2px 10px;font-size:14px}
.fab{position:fixed;right:16px;bottom:calc(16px + env(safe-area-inset-bottom,0px));z-index:20;width:auto;margin:0;border-radius:99px;padding:14px 20px;background:var(--blue);color:#fff;font-size:16px;box-shadow:0 6px 18px rgba(20,22,58,.35)}
.chat{position:fixed;right:16px;bottom:calc(76px + env(safe-area-inset-bottom,0px));z-index:21;width:min(400px,calc(100vw - 32px));height:min(520px,calc(100% - 110px));background:var(--card);border:2px solid var(--tx);border-radius:20px;display:none;flex-direction:column;overflow:hidden}
.chat.on{display:flex}.chat header{padding:12px 16px;font:800 17px "Bricolage Grotesque",sans-serif;border-bottom:2px solid var(--tx)}
.msgs{flex:1;overflow-y:auto;padding:12px;display:flex;flex-direction:column;gap:8px}
.m{max-width:88%;padding:9px 12px;border-radius:14px;font-size:14px;background:var(--bg)}.m.u{align-self:flex-end;background:var(--blue);color:#fff}
.chips{display:flex;gap:6px;flex-wrap:wrap;padding:0 12px 8px}.chips span{font-size:12px;border:1.5px solid var(--bd);border-radius:99px;padding:3px 10px;cursor:pointer}
.cin{display:flex;gap:8px;padding:10px;border-top:2px solid var(--bd)}.cin button{width:auto;margin:0;padding:0 16px;font-size:15px}
.err{color:var(--coral);font-weight:600;margin-top:12px}.err:empty{display:none}
.how{margin-top:26px;box-shadow:4px 4px 0 var(--skip)}.how summary{margin:0;color:var(--tx)}.how p,.how li{font-size:14px;color:var(--mu)}.how code{background:var(--bg);padding:2px 6px;border-radius:6px;color:var(--tx)}
footer{margin-top:20px;padding-top:16px;border-top:2px solid var(--bd);font-size:13px;color:var(--mu)}
noscript{display:block;padding:16px;background:var(--coral);color:#fff}
@media(prefers-reduced-motion:reduce){*{animation:none!important}}
</style></head><body><main>
<noscript>This app needs JavaScript to run.</noscript>
<div class="top">BunkBudget<span>SRM Trichy · Odd Sem 2026-27</span></div>
<div class="hero"><div>
<h1>Know how many classes you can skip.</h1>
<p class="lead">Pick your section, type your attendance, and see every remaining class as a tile: attend it, or safely skip it.</p></div>
<div class="demo" aria-hidden="true"><i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i></div></div>

<section class="panel">
 <div class="grid">
  <div><label for="sec">Your section</label><select id="sec"></select></div>
  <div><label for="today">Today</label><input id="today" type="date"></div>
  <div><label for="plan">Plan up to this date</label><input id="plan" type="date"></div>
  <div><label for="lim">Minimum attendance (%)</label><input id="lim" type="number" value="75" min="1" max="100"></div>
 </div>
 <div id="subs"></div>
 <details><summary>Semester dates and holidays</summary>
  <div class="grid" style="margin-top:12px">
   <div><label for="start">Semester start</label><input id="start" type="date" value="2026-08-03"></div>
   <div><label for="end">Last working day</label><input id="end" type="date" value="2026-11-20"></div>
   <div><label for="cut">Recovery deadline</label><input id="cut" type="date" value="2026-10-31"></div>
  </div>
  <label for="hol" style="margin-top:12px">Holidays (YYYY-MM-DD, comma separated). Sundays are always off.</label>
  <textarea id="hol" rows="2">2026-08-15,2026-09-14,2026-10-02,2026-10-19,2026-10-20,2026-11-08</textarea>
  <label for="sat" style="margin-top:12px">Saturday is a working day?</label>
  <select id="sat"><option value="0">No</option><option value="1">Yes</option></select>
 </details>
 <div id="err" class="err" role="alert"></div>
 <button id="go">Show my bunk budget</button>
</section>
<div id="out" aria-live="polite"></div>
<details class="panel how"><summary>How the numbers work</summary>
<p>Classes held so far come from your section timetable, counting each period from the semester start to yesterday (Sundays and holidays excluded). Your attendance % is applied to that count.</p>
<p>To stay at or above a limit <code>T</code>, you must attend at least <code>T% × (held + left) − attended</code> of the remaining classes. If that number is larger than the classes left, the limit cannot be reached.</p>
<ul><li>OD and medical days count as present. Absent days count against you.</li><li>Irreversible detention means that even attending every class until the recovery deadline cannot reach the limit.</li><li>Timetable source: SEEE Odd Semester 2026-27 sheets, SRM Trichy.</li></ul></details>
<footer>BunkBudget is a student project and not an official SRM tool. Semester dates and holidays are editable estimates. Always confirm your final attendance with your faculty or the college portal.</footer>
<button class="fab" id="fab" aria-label="Open Attendance Advisor">Ask Advisor</button>
<div class="chat" id="chat" role="dialog" aria-label="Attendance Advisor"><header>Attendance Advisor</header><div class="msgs" id="msgs"></div>
<div class="chips" id="chips"><span>If I take a 3-day sick leave starting tomorrow, will I fall below the limit?</span><span>Which subject is most at risk?</span><span>Can I skip 2 days and stay safe?</span></div>
<div class="cin"><input id="cq" placeholder="Ask about your attendance" aria-label="Question"><button id="csend">Send</button></div></div><script>
const RAW={
"II ECE-DS A":[{A:"Transforms & Boundary Value Problems",B:"Solid State Devices",C:"Computer Organization & Architecture",D:"Digital Logic Design",E:"EM Theory & Interference",F:"Professional Ethics",G:"Universal Human Values-II",H:"Verbal Reasoning",I:"Social Engineering",L:"Devices & Digital IC Lab"},["EAII-GGLL","CAED-GGHH","ABCD--H--","BCAF-LL--","DBEC-----"]],
"II ECE-DS B":[{A:"Transforms & Boundary Value Problems",B:"Solid State Devices",C:"Computer Organization & Architecture",D:"Digital Logic Design",E:"EM Theory & Interference",F:"Professional Ethics",G:"Universal Human Values-II",H:"Verbal Reasoning",I:"Social Engineering",L:"Devices & Digital IC Lab"},["--LL-DBCI","LL---CDEA","G----IEAD","GGHH-ACBE","H----FABC"]],
"II BME":[{A:"Transforms & Boundary Value Problems",B:"Biomedical Signals & Systems",C:"Electric & Electronic Circuits",D:"Digital Logic for Medical Systems",E:"Medical Physics",F:"Professional Ethics",G:"Universal Human Values-II",H:"Verbal Reasoning",I:"Social Engineering",L:"DLMS / EEC Lab"},["ECII-LL--","CEBA-HH--","BDA--HG--","AEBD---LL","FACD---GG"]],
"III ECE-DS":[{A:"Discrete Mathematics",B:"Microprocessor & Microcontroller",C:"VLSI Design & Technology",D:"Machine Learning for All",E:"Database Design & Management",F:"Community Connect",G:"Analytical & Logical Thinking",H:"Indian Art Form",L:"VLSI / Microprocessor Lab",P:"B-Proj"},["EBCA-----","CBDF-LL--","HBAC---GG","ADEF-----","DAEP-G-LL"]],
"III ECE-A":[{A:"Discrete Mathematics",B:"Microprocessor & Microcontroller",C:"VLSI Design & Technology",D:"System & Network on Chip",E:"Machine Learning for All",F:"Community Connect",G:"Analytical & Logical Thinking",H:"Indian Art Form",L:"VLSI / Microprocessor Lab",P:"B-Proj"},["EBBA-GG--","HDBP--G--","CADF---LL","AECF-----","DAEC-LL--"]],
"III ECE-B":[{A:"Discrete Mathematics",B:"Microprocessor & Microcontroller",C:"VLSI Design & Technology",D:"System & Network on Chip",E:"Machine Learning for All",F:"Community Connect",G:"Analytical & Logical Thinking",H:"Indian Art Form",L:"VLSI / Microprocessor Lab",P:"B-Proj"},["LL---EBAD","GG---FBDC","G----PBAH","LL---ACEF","-----CAED"]],
"III BME":[{A:"Probability & Statistics",B:"Microcontrollers & Applications",C:"Biomedical Signal Processing",D:"Biometrics",E:"Modern Wireless Comm.",F:"Principles of Medical Imaging",G:"Analytical & Logical Thinking",H:"Indian Art Form",I:"Community Connect",L:"MPMC / Bio-DSP Lab"},["GGLL-EBFH","LLG--CDAB","-----CAFD","---I-ACEB","I----FADE"]],
"IV ECE-A":[{A:"Behavioural Psychology",B:"Wireless Comm. & Antenna",C:"Computer Comm. & Network Security",D:"Semiconductor Memory Design",E:"Scripting Lang. for EDA",F:"Machine Learning for All",L:"CCNS Lab"},["C-AD-----","CDBF-----","BLEF-----","FAEB-----","CADE-----"]],
"IV ECE-B":[{A:"Behavioural Psychology",B:"Wireless Comm. & Antenna",C:"Computer Comm. & Network Security",D:"Semiconductor Memory Design",E:"Scripting Lang. for EDA",F:"Machine Learning for All",L:"CCNS Lab"},["CAEF-----","CEFB-----","CDAB-----","DBLA-----","EDF------"]]
};
// Build SEC[section][subject] = classes per weekday [Sun..Sat] from the slot grids
const SEC={};
for(const [k,[names,grid]] of Object.entries(RAW)){SEC[k]={};
 grid.forEach((row,di)=>{for(const ch of row){if(ch==="-")continue;const n=names[ch];
  (SEC[k][n]=SEC[k][n]||[0,0,0,0,0,0,0])[di+1]++;}});}
let LV=[],SMP=null,H=[],D=[],X={},SUM="";const $=id=>document.getElementById(id);
const iso=d=>d.getFullYear()+"-"+String(d.getMonth()+1).padStart(2,"0")+"-"+String(d.getDate()).padStart(2,"0");
const pd=s=>new Date(s+"T12:00:00");
const t=new Date();$("today").value=iso(t);
const p=new Date(t);p.setDate(p.getDate()+14);$("plan").value=iso(p);
Object.keys(SEC).forEach(k=>$("sec").add(new Option(k,k)));
function drawSubs(){$("subs").innerHTML=Object.keys(SEC[$("sec").value]).map(s=>
 `<div class="subj"><div><label>Subject</label><input value="${s}" disabled></div><div><label>Attendance %</label><input class="pct-in" type="number" min="0" max="100" step="0.1" value="80"></div></div>`).join("");}
$("sec").onchange=drawSubs;
try{const sv=JSON.parse(localStorage.getItem("bb")||"null");if(sv&&SEC[sv.s]){$("sec").value=sv.s;drawSubs();document.querySelectorAll(".pct-in").forEach((e,i)=>{if(sv.p[i]!=null)e.value=sv.p[i]})}else drawSubs()}catch(e){drawSubs()}
function drawWI(){const N=+$("skip").value,e=new Date(X.today);e.setDate(e.getDate()+N-1);let h="",ks=0;
 D.forEach(o=>{const sk=Math.min(count(o.d,X.today,e,X.hol,X.sat),o.Re),pr=(o.a+o.Re-sk)/(o.C+o.Re)*100;ks+=sk;
  h+=`<div class="row"><span>${o.n}</span><div class="bar"><i style="width:${Math.min(pr,100)}%;background:${pr>=X.L?"var(--mint)":"var(--coral)"}"></i><b style="left:${X.L}%"></b></div><b>${pr.toFixed(1)}%</b></div>`;});
 $("wi").innerHTML=`<p class="note" style="margin:6px 0 0">${N===0?"Drag the slider to skip upcoming days.":`Skipping the next ${N} day${N>1?"s":""} (${ks} classes) and attending everything after. The line marks ${X.L}%.`}</p>${h}`;}
function count(days,from,to,hol,sat){let n=0;const d=new Date(from);
 while(d<=to){const w=d.getDay();if(w!==0&&!hol.has(iso(d))&&(w!==6||sat))n+=days[w];d.setDate(d.getDate()+1);}return n;}
const need=(a,C,R,T)=>Math.max(0,Math.ceil(T/100*(C+R)-a-1e-9));
const fmt=(x,R,label)=>x>R?`<span class="tag r">Not possible</span>`:x===0?`<span class="tag gr">Safe: skip all ${R}</span>`:`Attend <b>${x}</b> of ${R}, skip ${R-x}`;
$("go").onclick=()=>{
 const badV=[...document.querySelectorAll(".pct-in")].some(e=>e.value===""||+e.value<0||+e.value>100),badD=pd($("today").value)>pd($("end").value)||pd($("plan").value)<pd($("today").value);
 $("err").textContent=badV?"Enter an attendance between 0 and 100 for every subject.":badD?"Check your dates: the plan date must be today or later, and today must be before the last working day.":"";
 if(badV||badD)return;
 const today=pd($("today").value),plan=pd($("plan").value),end=pd($("end").value),start=pd($("start").value),cut=pd($("cut").value);
 const hol=new Set($("hol").value.split(",").map(s=>s.trim()).filter(Boolean)),sat=$("sat").value==="1",L=+$("lim").value;
 const y=new Date(today);y.setDate(y.getDate()-1);
 const subs=SEC[$("sec").value],names=Object.keys(subs),pcts=[...document.querySelectorAll(".pct-in")].map(e=>+e.value);
 D=[];SUM="";const items=[];let tot=0,totPlan=0,budget=0,cards="",doomed=[];
 names.forEach((n,i)=>{const d=subs[n];
  const C=count(d,start,y,hol,sat),Re=count(d,today,end,hol,sat),Rp=count(d,today,plan,hol,sat),Rc=count(d,today,cut,hol,sat);
  const a=pcts[i]/100*C,x=need(a,C,Re,L),x9=need(a,C,Re,90),xp=need(a,C,Rp,L);
  tot+=Re;totPlan+=Rp;
  const lost=need(a,C,Rc,L)>Rc;if(lost)doomed.push(`${n} (best ${((a+Rc)/(C+Rc)*100).toFixed(1)}% by ${$("cut").value})`);
  if(!lost&&x<=Re)budget+=Re-x;
  const bad=x>Re;let tiles="";
  for(let k=0;k<Re;k++){const c=bad?"x":k<x?"":k<Math.min(Re,Math.max(x,x9))?"g":"s";tiles+=`<i class="t ${c}" style="--i:${Math.min(k,60)}"></i>`;}
  const best=((a+Re)/(C+Re)*100).toFixed(1);
  const r=lost||bad?9:x/Math.max(Re,1),lb=lost||bad?"Lost":r>.7?"High risk":r>.3?"Watch":"Safe";D.push({n,a,C,Re,d,pct:pcts[i]});SUM+=`${n}: ${pcts[i]}% now, ${bad?"cannot reach "+L+"%":"attend "+x+"/"+Re+" to stay above "+L+"%"}\n`;
  items.push({r,h:`<article class="sc ${lost||bad?"bad":x===0?"ok":""}"><header><h3>${n}<span class="chip">${lb}</span></h3><div class="pct">${pcts[i]}%<small>now</small></div></header>
  <div class="strip" aria-label="${Re} classes left">${tiles}</div>
  <ul class="facts"><li>By ${$("plan").value}: ${fmt(xp,Rp)}</li>
  <li>By semester end: ${fmt(x,Re)}</li>
  <li>${x9>Re?`Reaching 90% is not possible (best ${best}%)`:`For 90%: attend <b>${x9}</b> of ${Re}`}</li></ul></article>`});});
 cards=items.sort((u,v)=>v.r-u.r).map(o=>o.h).join("");X={today,hol,sat,L,end,start};
 let h="";
 if(doomed.length)h+=`<div class="alert" role="alert"><span class="big">Irreversible detention</span>Even if you attend every class until ${$("cut").value}, you cannot reach ${L}% in ${doomed.join("; ")}. Meet your faculty or HoD about condonation now.</div>`;
 h+=`<div class="stats"><div class="stat"><b>${Math.max(0,Math.min(100,Math.round((today-start)/(end-start)*100)))}%</b><span>of the semester is over<div class="prog"><i style="width:${Math.max(0,Math.min(100,(today-start)/(end-start)*100))}%"></i></div></span></div><div class="stat"><b>${tot}</b><span>classes left this semester</span></div><div class="stat"><b>${totPlan}</b><span>classes until ${$("plan").value}</span></div><div class="stat"><b>${budget}</b><span>classes you can skip in total and stay above ${L}%</span></div></div>
 <div class="legend"><span><i class="t"></i>Must attend</span><span><i class="t g"></i>Attend to reach 90%</span><span><i class="t s"></i>Safe to skip</span><span><i class="t x"></i>Lost</span></div><section class="panel wi"><h3>What if I skip the next few days?</h3><input id="skip" type="range" min="0" max="30" value="0" aria-label="Days to skip"><div id="wi"></div></section><button class="ghost" id="copy">Copy summary to share</button><div id="extras"></div><div class="cards">${cards}</div>`;
 $("out").innerHTML=h;LV=[];mountExtras();$("skip").oninput=drawWI;drawWI();
 $("copy").onclick=async()=>{try{await navigator.clipboard.writeText("My attendance plan ("+$("sec").value+")\n"+SUM);$("copy").textContent="Copied";}catch(e){$("copy").textContent="Copy not allowed here";}};
 try{localStorage.setItem("bb",JSON.stringify({s:$("sec").value,p:pcts}))}catch(e){}
 $("out").scrollIntoView({behavior:"smooth"});
};

const ymd=(d,n)=>{const e=new Date(d);e.setDate(e.getDate()+n);return e};
function sim(o,lvs){let a=o.a,lost=0;const y=ymd(X.today,-1);
 lvs.forEach(l=>{const f=pd(l.from),t=pd(l.to),pe=t<y?t:y;
  if(f<=pe&&l.type!=="absent")a+=count(o.d,f,pe,X.hol,X.sat);
  const fs=f>X.today?f:X.today;if(fs<=t&&l.type==="absent")lost+=count(o.d,fs,t,X.hol,X.sat);});
 a=Math.min(a,o.C);lost=Math.min(lost,o.Re);const den=Math.max(1,o.C+o.Re);
 return{cur:a/Math.max(1,o.C)*100,fin:(a+o.Re-lost)/den*100,lost}}
function mountExtras(){$("extras").innerHTML=`<div class="two"><section class="panel"><h3 style="margin:0 0 8px;font-size:22px">Attendance health</h3><div id="charts"></div></section>
<section class="panel"><h3 style="margin:0 0 4px;font-size:22px">OD and leave simulator</h3><p class="note" style="margin:0 0 10px">OD and medical days count as present. Absent days count against you. Past OD days add back classes marked absent.</p>
<div class="grid"><div><label for="lt">Type</label><select id="lt"><option value="od">On-Duty (OD)</option><option value="medical">Medical leave</option><option value="absent">Absent / personal leave</option></select></div>
<div><label for="lf">From</label><input id="lf" type="date" value="${iso(X.today)}"></div><div><label for="ltd">To</label><input id="ltd" type="date" value="${iso(X.today)}"></div></div>
<button id="ladd" style="margin-top:12px;padding:11px;font-size:16px">Add days</button><div id="llist"></div><div id="lres"></div></section></div>`;
 $("ladd").onclick=()=>{const f=$("lf").value,t=$("ltd").value;if(!f||!t||t<f)return;LV.push({type:$("lt").value,from:f,to:t});drawAll();};drawAll();}
function drawAll(){const nm={od:"OD",medical:"Medical",absent:"Absent"};
 $("llist").innerHTML=LV.map((l,i)=>`<div class="lrow"><span><b>${nm[l.type]}</b> ${l.from} to ${l.to}</span><button class="ghost" data-i="${i}" aria-label="Remove">Remove</button></div>`).join("");
 document.querySelectorAll("#llist button").forEach(b=>b.onclick=()=>{LV.splice(+b.dataset.i,1);drawAll();});
 const R=D.map(o=>({n:o.n,b:sim(o,[]),z:sim(o,LV)}));
 $("lres").innerHTML=R.map(r=>{const dl=r.z.fin-r.b.fin;return `<div class="row"><span>${r.n}</span><div class="bar"><i style="width:${Math.min(r.z.fin,100)}%;background:${r.z.fin>=X.L?"var(--mint)":"var(--coral)"}"></i><b style="left:${X.L}%"></b></div><b>${r.z.fin.toFixed(1)}%${LV.length?`<small style="color:var(--mu)"> (${dl>=0?"+":""}${dl.toFixed(1)})</small>`:""}</b></div>`}).join("")+`<p class="note" style="margin:8px 0 0">Final percentage at semester end if you attend every other class.</p>`;
 charts(R)}
function charts(R){const n=R.length,avg=R.reduce((s,r)=>s+r.z.fin,0)/Math.max(n,1),g=R.filter(r=>r.z.fin>=90).length,y=R.filter(r=>r.z.fin>=X.L&&r.z.fin<90).length,rd=n-g-y,C=2*Math.PI*52;
 let off=0;const seg=(c,v)=>{const l=v/Math.max(n,1)*C,e=`<circle r="52" cx="70" cy="70" fill="none" stroke="${c}" stroke-width="22" stroke-dasharray="${l} ${C-l}" stroke-dashoffset="${-off}" transform="rotate(-90 70 70)"/>`;off+=l;return e};
 const bars=R.map((r,i)=>{const yy=8+i*34,w=v=>Math.min(v,100)*3.2;return `<text x="0" y="${yy+9}" font-size="11" fill="var(--mu)">${r.n.length>22?r.n.slice(0,21)+"…":r.n}</text><rect x="0" y="${yy+13}" width="${w(r.b.cur)}" height="6" rx="3" fill="var(--skip)"/><rect x="0" y="${yy+21}" width="${w(r.z.fin)}" height="8" rx="4" fill="${r.z.fin>=X.L?"var(--mint)":"var(--coral)"}"/><text x="${w(Math.max(r.b.cur,r.z.fin))+6}" y="${yy+29}" font-size="11" fill="var(--tx)">${r.z.fin.toFixed(0)}%</text>`}).join("");
 $("charts").innerHTML=`<div style="display:flex;gap:16px;align-items:center;flex-wrap:wrap"><svg width="140" height="140" viewBox="0 0 140 140" role="img" aria-label="Health ${avg.toFixed(0)} percent"><circle r="52" cx="70" cy="70" fill="none" stroke="var(--skip)" stroke-width="22"/>${seg("var(--mint)",g)}${seg("var(--gold)",y)}${seg("var(--coral)",rd)}<text x="70" y="70" text-anchor="middle" font-size="26" font-weight="800" fill="var(--tx)" font-family="Bricolage Grotesque,sans-serif">${avg.toFixed(0)}%</text><text x="70" y="88" text-anchor="middle" font-size="10" fill="var(--mu)">projected avg</text></svg>
 <div class="leg2" style="flex-direction:column"><span><i class="t" style="background:var(--mint)"></i>${g} above 90%</span><span><i class="t g"></i>${y} between ${X.L}% and 90%</span><span><i class="t" style="background:var(--coral)"></i>${rd} below ${X.L}%</span></div></div>
 <svg viewBox="0 0 380 ${n*34+14}" width="100%" style="margin-top:14px" role="img" aria-label="Attendance by subject">${bars}<line x1="${X.L*3.2}" x2="${X.L*3.2}" y1="0" y2="${n*34+8}" stroke="var(--tx)" stroke-dasharray="3 3"/></svg>
 <div class="leg2"><span><i class="t" style="background:var(--skip)"></i>Now</span><span><i class="t" style="background:var(--mint)"></i>Final (with your leaves)</span><span>Dashed line: ${X.L}%</span></div>`}
// ---- Attendance Advisor ----
try{if(window.claude&&claude.use)claude.use("sample").then(x=>{SMP=x}).catch(()=>{})}catch(e){}
function findSubj(q){q=q.toLowerCase();return D.filter(o=>o.n.toLowerCase().split(/[^a-z]+/).some(w=>w.length>3&&q.includes(w.slice(0,5))))}
function simTool(a){const q=(a.subject||"").toLowerCase();let list=q&&q!=="all"?findSubj(q):D;
 if(q&&q!=="all"&&!list.length)return{error:"Subject not found",available:D.map(o=>o.n)};
 const f=a.start_date||iso(ymd(X.today,1)),days=Math.max(1,+a.days||1),t=iso(ymd(pd(f),days-1)),ex=a.kind==="absent"?"absent":a.kind||"absent";
 return{limit:X.L,window:f+" to "+t,results:list.map(o=>{const b=sim(o,[]),ab=sim(o,[{type:"absent",from:f,to:t}]),cl=count(o.d,pd(f)>X.today?pd(f):X.today,pd(t),X.hol,X.sat);
  return{subject:o.n,current_pct:+b.cur.toFixed(1),classes_in_window:cl,final_pct_if_absent:+ab.fin.toFixed(1),final_pct_if_excused_OD_or_medical:+b.fin.toFixed(1),final_pct_if_absent_below_limit:ab.fin<X.L,final_pct_without_leave:+b.fin.toFixed(1),classes_left_in_semester:o.Re}})}}
function local(q){const l=q.toLowerCase();
 if(/risk|worst|danger|weak/.test(l)){const r=D.map(o=>({n:o.n,f:sim(o,LV).fin})).sort((a,b)=>a.f-b.f)[0];return `**${r.n}** is your weakest subject, heading for ${r.f.toFixed(1)}% by semester end (limit ${X.L}%).`}
 const days=+(l.match(/(\d+)\s*-?\s*day/)||l.match(/(\d+)/)||[0,1])[1]||1,od=/\bod\b|on.?duty/.test(l),med=/medical/.test(l);
 const st=/today/.test(l)?iso(X.today):(l.match(/\d{4}-\d{2}-\d{2}/)||[iso(ymd(X.today,1))])[0];
 const subj=findSubj(l),r=simTool({subject:subj.length===1?subj[0].n:"all",start_date:st,days});
 if(r.error)return `I couldn't find that subject. Your subjects are: ${r.available.join(", ")}.`;
 const bad=r.results.filter(x=>x.final_pct_if_absent_below_limit);
 let t=`For ${days} day${days>1?"s":""} from ${st}:\n`+r.results.map(x=>`- ${x.subject}: ${x.classes_in_window} classes missed, ${x.current_pct}% now, ${x.final_pct_if_absent}% at semester end`).join("\n");
 if(od||med)t+=`\nAs ${od?"OD":"medical leave"} these count as present, so your final % stays unchanged.`;
 else t+=bad.length?`\nWarning: this pushes ${bad.map(x=>x.subject).join(", ")} below ${X.L}%. Get a medical certificate or OD approval if you can.`:`\nYou stay above ${X.L}% in every subject you asked about.`;return t}
const fmtMsg=t=>t.replace(/&/g,"&amp;").replace(/</g,"&lt;").replace(/\*\*(.+?)\*\*/g,"<b>$1</b>").replace(/\n/g,"<br>");
function addMsg(t,u){const m=document.createElement("div");m.className="m"+(u?" u":"");m.innerHTML=fmtMsg(t);$("msgs").appendChild(m);$("msgs").scrollTop=1e9;return m}
async function ask(q){if(!D.length){$("go").click();}if(!D.length)return "Enter your attendance first.";
 if(SMP){try{const ctx=D.map(o=>({subject:o.n,current_pct:o.pct,classes_held:o.C,classes_left:o.Re}));
  const inp=`You are Attendance Advisor for an SRM Trichy student. Today is ${iso(X.today)}, minimum attendance ${X.L}%, semester ends ${iso(X.end)}. Dashboard: ${JSON.stringify(ctx)}. Leaves already planned: ${JSON.stringify(LV)}. Always call the simulate tool for any number and never do the math yourself. "Tomorrow" is ${iso(ymd(X.today,1))}. Sick leave without a certificate counts as absent. Reply in at most 5 short sentences with the exact numbers, a clear warning if any subject drops below the limit, and one practical tip. If a subject is not in the dashboard, say so and list the available ones.\nRecent chat: ${H.slice(-4).join(" | ")}\nQuestion: ${q}`;
  const r=await SMP(inp,{cache:false,tools:[{name:"simulate",description:"Project attendance if the student is absent, on OD or on medical leave for consecutive calendar days.",inputSchema:{type:"object",properties:{subject:{type:"string",description:"Subject name or 'all'"},start_date:{type:"string",description:"YYYY-MM-DD"},days:{type:"number"},kind:{type:"string",enum:["absent","od","medical"]}},required:["days"]},execute:simTool}]});
  if(r&&r.text)return r.text}catch(e){}}
 return local(q)}
async function send(q){q=(q||$("cq").value).trim();if(!q)return;$("cq").value="";$("chips").style.display="none";addMsg(q,1);const w=addMsg("Working out the numbers…");
 const a=await ask(q);H.push("Q:"+q,"A:"+a.slice(0,200));w.innerHTML=fmtMsg(a);$("msgs").scrollTop=1e9}
$("fab").onclick=()=>{$("chat").classList.toggle("on");if(!$("msgs").children.length)addMsg("Hi! Ask me about leaves, OD or how many classes you can skip. I use the numbers on your dashboard.")};
$("csend").onclick=()=>send();$("cq").onkeydown=e=>{if(e.key==="Enter")send()};
document.querySelectorAll("#chips span").forEach(c=>c.onclick=()=>send(c.textContent));
</script></main></body></html>
