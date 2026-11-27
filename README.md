[transport_game (2).html](https://github.com/user-attachments/files/35516015/transport_game.2.html)
<!DOCTYPE html>
<html lang="ar" dir="rtl"><head><meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>معرض ركّاب مصر</title>
<style>
*{box-sizing:border-box;-webkit-tap-highlight-color:transparent}
body{margin:0;font-family:'Segoe UI',Tahoma,Arial,sans-serif;background:linear-gradient(#ffe9b8,#bfe8ee 60%,#e9d3a6);min-height:100vh;color:#2b3a4a;overflow-x:hidden}
.scr{display:none;min-height:100vh;padding:14px;max-width:760px;margin:auto;animation:in .4s}
.scr.on{display:block}
@keyframes in{from{opacity:0;transform:translateY(18px)}to{opacity:1;transform:none}}
.ground{position:fixed;bottom:0;left:0;right:0;height:26px;background:repeating-linear-gradient(90deg,#8a6a3b 0 30px,#a98450 30px 60px);z-index:-1}
h1{font-size:2.1rem;margin:10px 0;color:#c2410c;text-align:center}
h2{font-size:1.35rem;line-height:1.7;margin:8px 0 14px}
.big{font-size:3rem;text-align:center;letter-spacing:6px;animation:fl 3s infinite ease-in-out}
@keyframes fl{50%{transform:translateY(-8px)}}
.sub{text-align:center;font-size:1.15rem;margin-bottom:18px}
.card{background:#fff;border-radius:22px;padding:18px;box-shadow:0 6px 0 #d9b76a,0 10px 24px #0002;margin:12px 0;border:3px solid #f3c969}
input{width:100%;font-size:1.3rem;padding:14px;border-radius:16px;border:3px solid #0e7490;text-align:center;font-family:inherit;margin-bottom:14px}
.btn,.opt{display:block;width:100%;font-family:inherit;font-size:1.3rem;font-weight:700;padding:16px;border:0;border-radius:18px;cursor:pointer;margin:10px 0;min-height:58px}
.btn{background:#f97316;color:#fff;box-shadow:0 5px 0 #c2410c}
.btn:active{transform:translateY(4px);box-shadow:0 1px 0 #c2410c}
.opt{background:#e0f2fe;color:#0c4a6e;box-shadow:0 5px 0 #7dd3fc;text-align:right}
.opt:disabled{opacity:.45;background:#fee2e2;box-shadow:none}
.mute{position:fixed;top:10px;left:10px;z-index:30;width:50px;height:50px;border-radius:50%;border:0;background:#fff;font-size:1.5rem;box-shadow:0 3px 8px #0003;cursor:pointer}
#hud{display:flex;gap:8px;align-items:center;justify-content:space-between;background:#0e7490;color:#fff;border-radius:18px;padding:10px 14px;font-weight:700;margin:50px 0 6px}
#hud span{font-size:1.1rem}
#tm.lo{background:#dc2626;border-radius:10px;padding:2px 10px;animation:pu .6s infinite}
@keyframes pu{50%{transform:scale(1.15)}}
.qn{color:#c2410c;font-weight:700}
.hall{display:flex;align-items:center;gap:12px;background:#fff;border-radius:18px;padding:14px;margin:10px 0;border:3px solid #cbd5e1;font-size:1.15rem;font-weight:700}
.hall i{font-style:normal;font-size:2rem}
.hall.d{border-color:#16a34a;background:#dcfce7}
.cols{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.mc{background:#fff7ed;border:3px solid #fdba74;border-radius:16px;padding:12px 8px;font-size:1.05rem;font-weight:700;text-align:center;cursor:pointer;margin:8px 0;min-height:72px;display:flex;align-items:center;justify-content:center;font-family:inherit}
.mc.sel{border-color:#0e7490;background:#cffafe;transform:scale(1.04)}
.mc.era{background:#ecfccb;border-color:#a3e635}
.mc.fin{color:#fff;border-color:transparent}
.mc.x{border-style:dashed;opacity:.8}
.hint{text-align:center;color:#b45309;min-height:26px;font-weight:700}
.ov{position:fixed;inset:0;background:#0007;display:none;align-items:center;justify-content:center;z-index:40;padding:16px}
.ov.on{display:flex}
.fbx{background:#fff;border-radius:26px;padding:22px;max-width:460px;width:100%;text-align:center;animation:pop .35s;border-top:12px solid}
.ok .fbx{border-color:#16a34a}.half .fbx{border-color:#eab308}.retry .fbx,.time .fbx{border-color:#f97316}.no .fbx{border-color:#64748b}
@keyframes pop{from{transform:scale(.6);opacity:0}}
#fbi{font-size:4rem}.ok #fbi{animation:bn .6s 2}.retry #fbi,.no #fbi,.time #fbi{animation:sh .5s}
@keyframes bn{50%{transform:translateY(-18px) rotate(10deg)}}
@keyframes sh{25%{transform:translateX(-10px)}75%{transform:translateX(10px)}}
#fbt{font-size:1.5rem;font-weight:800;margin:6px 0}
#fbp{font-size:1.3rem;color:#15803d;font-weight:800}
#fbx{font-size:1.1rem;line-height:1.8;margin:8px 0}
.st{position:fixed;font-size:1.8rem;z-index:50;pointer-events:none;animation:rise 1.6s forwards}
@keyframes rise{from{opacity:1;transform:translateY(0) rotate(0)}to{opacity:0;transform:translateY(-70vh) rotate(360deg)}}
.stats{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin:14px 0}
.stats div{background:#fef3c7;border-radius:14px;padding:12px;text-align:center;font-weight:700}
.stars{font-size:3rem;text-align:center;color:#f59e0b}
body.h0{background:linear-gradient(#fde68a,#fdba74)}body.h1{background:linear-gradient(#d9f99d,#86efac)}body.h2{background:linear-gradient(#bae6fd,#67e8f9)}body.hf{background:linear-gradient(#e9d5ff,#fbcfe8)}
#pb{height:12px;background:#fff9;border-radius:8px;overflow:hidden;margin:4px 0}#pbi{display:block;height:100%;width:0;background:#f97316;transition:width .5s}
.rd{background:#fef3c7;border:2px solid #f59e0b;border-radius:14px;font-family:inherit;font-size:1.05rem;padding:10px 16px;cursor:pointer;margin-bottom:10px;min-height:48px}
.pp{position:fixed;top:30%;left:50%;transform:translateX(-50%);font-size:3rem;font-weight:900;color:#16a34a;z-index:60;text-shadow:0 3px 0 #fff;pointer-events:none;animation:pp 1.4s forwards}
@keyframes pp{from{opacity:1;transform:translate(-50%,0) scale(.6)}to{opacity:0;transform:translate(-50%,-90px) scale(1.4)}}
.retry .fbx,.no .fbx,.time .fbx{background:#fff1f2}.ok .fbx{background:#f0fdf4}
@media print{.mute,.btns,.ov,.ground,.st,.pp{display:none!important}body{background:#fff!important}.scr{padding:0;max-width:none;min-height:0}}
.btns{max-width:520px;margin:10px auto}
</style></head><body>
<div class="ground"></div>
<button class="mute" id="mu" aria-label="الصوت">🔊</button>

<div class="scr on" id="s0">
 <div class="big">🐎🚂🚢🚝</div>
 <h1>معرض ركّاب مصر</h1>
 <p class="sub">ادخل أجنحة المعرض واكتشف كيف تطورت وسائل النقل في بلادنا! 🌟</p>
 <div class="card"><input id="nm" placeholder="اكتب اسمك هنا" maxlength="20"><div class="hint" id="nh"></div>
 <button class="btn" id="go">ابدأ اللعب 🎮</button></div>
</div>

<div class="scr" id="s1"><h1>🏛️ مراحل المعرض</h1><div id="hl"></div><button class="btn" id="hn"></button></div>

<div class="scr" id="s2"><div id="hud"><span id="ht"></span><span id="sc">⭐ 0</span><span id="tm">⏱ 30</span></div><div id="pb"><i id="pbi"></i></div><div id="stage"></div></div>

<div class="scr" id="s3"><div id="cert"></div><div class="btns"><button class="btn" id="pr">🖨️ طباعة الشهادة / حفظ PDF</button><button class="btn" id="dl">⬇️ تحميل الشهادة</button><button class="btn" id="nx"></button></div></div>

<div class="ov" id="fb"><div class="fbx"><div id="fbi"></div><div id="fbt"></div><div id="fbp"></div><div id="fbx"></div><button class="btn" id="fbb"></button></div></div>

<script>
const TF=[
{q:"تُعد مصر من أواخر الدول التي استخدمت السكك الحديدية.",a:false,e:"مصر من أوائل الدول التي استخدمت السكك الحديدية، فقد أُنشئ أول خط بين القاهرة والإسكندرية."},
{q:"استخدم المصريون القدماء الزحافات والدواب للنقل البري.",a:true,e:"استخدم المصريون القدماء الزحافات والدواب لنقل الأحمال الثقيلة والبضائع."},
{q:"يُعتبر المونوريل من وسائل النقل الصديقة للبيئة.",a:true,e:"يعمل المونوريل بالكهرباء، فلا يُنتج دخانًا ويحافظ على نظافة الهواء."}];
const MC=[
{q:"ربط أول خط سكة حديد في مصر بين القاهرة و...",o:["السويس","الإسكندرية","أسوان"],a:1,e:"ربط أول خط سكة حديد في مصر بين القاهرة والإسكندرية."},
{q:"من وسائل النقل المائية قديمًا:",o:["الطائرات","الزحافات","القوارب الخشبية"],a:2,e:"كان المصريون القدماء يبحرون في نهر النيل بالقوارب الخشبية، أما الزحافات فللنقل البري."}];
const MT=[{t:"🐎 العربات الحربية",e:0},{t:"🚂 أول خط سكة حديد",e:1},{t:"🚝 المونوريل والقطار الكهربائي",e:2}];
const ER=["المصريون القدماء","العصر الحديث","العصر المعاصر"],EO=[1,2,0];
const COL=["#db2777","#0891b2","#7c3aed"];
const MAX=(TF.length+MT.length+MC.length)*10;
const HALLS=[["🏛️","المرحلة الأولى: تحدي الصح والخطأ"],["🚂","المرحلة الثانية: تحدي التوصيل والمطابقة"],["🚢","المرحلة الثالثة: تحدي الاختيار من متعدد"],["🎓","شهادة تقدير بعد كل مرحلة، وشهادة نهائية في الختام"]];
const SN=["تحدي الصح والخطأ","تحدي التوصيل والمطابقة","تحدي الاختيار من متعدد"],SM=[TF.length*10,MT.length*10,MC.length*10];
const $=id=>document.getElementById(id);
let S,AC,master,muted=false,T={l:0,iv:null,cb:null};
function reset(){S={n:S?S.n:"",sc:0,ok:0,fail:0,f:0,h:0,ps:[0,0,0],cur:0,d:[0,0,0]};$("sc").textContent="⭐ 0";$("pbi").style.width="0"}
function show(id){document.querySelectorAll(".scr").forEach(s=>s.classList.toggle("on",s.id==id));window.scrollTo(0,0)}
/* الصوت */
function init(){try{if(!AC)AC=new(window.AudioContext||window.webkitAudioContext)();if(AC.state==="suspended")AC.resume()}catch(e){}}
function snd(f){if(muted||!AC)return;try{if(master)master.disconnect();master=AC.createGain();master.gain.value=.5;master.connect(AC.destination);f(AC.currentTime)}catch(e){}}
function tn(fr,t,d,ty,v){const o=AC.createOscillator(),g=AC.createGain();o.type=ty||"sine";o.frequency.value=fr;g.gain.setValueAtTime(v||.3,t);g.gain.exponentialRampToValueAtTime(.001,t+d);o.connect(g);g.connect(master);o.start(t);o.stop(t+d)}
const clap=()=>snd(t=>{for(let i=0;i<8;i++){const n=Math.floor(AC.sampleRate*.08),b=AC.createBuffer(1,n,AC.sampleRate),d=b.getChannelData(0);for(let j=0;j<n;j++)d[j]=(Math.random()*2-1)*(1-j/n);const s=AC.createBufferSource(),f=AC.createBiquadFilter(),g=AC.createGain();f.type="bandpass";f.frequency.value=1800;s.buffer=b;g.gain.value=.7;s.connect(f);f.connect(g);g.connect(master);s.start(t+i*.11+Math.random()*.03)}tn(784,t,.15,"triangle",.2);tn(1046,t+.15,.3,"triangle",.2)});
const good=()=>snd(t=>[523,659,784].forEach((f,i)=>tn(f,t+i*.12,.25,"triangle",.3)));
const bad=()=>snd(t=>{tn(300,t,.18,"sine",.25);tn(240,t+.18,.25,"sine",.25)});
const fan=()=>snd(t=>[523,659,784,1046,784,1046,1318].forEach((f,i)=>tn(f,t+i*.14,.3,"triangle",.3)));
$("mu").onclick=()=>{init();muted=!muted;$("mu").textContent=muted?"🔇":"🔊"};
function say(t){try{speechSynthesis.cancel();const u=new SpeechSynthesisUtterance(t);u.lang="ar-EG";speechSynthesis.speak(u)}catch(e){}}
const blip=()=>snd(t=>{tn(660,t,.12,"triangle",.2);tn(880,t+.1,.18,"triangle",.2)});
/* المؤقت */
function upd(){const e=$("tm");e.textContent="⏱ "+T.l;e.classList.toggle("lo",T.l<=10)}
function tStop(){clearInterval(T.iv);T.iv=null}
function tRun(){tStop();T.iv=setInterval(()=>{T.l--;upd();if(T.l<=0){tStop();T.cb()}},1000)}
function tStart(s,cb){T.l=s;T.cb=cb;upd();tRun()}
/* التغذية الراجعة */
function burst(n){for(let i=0;i<n;i++){const s=document.createElement("span");s.className="st";s.textContent="⭐";s.style.left=Math.random()*90+"vw";s.style.bottom=Math.random()*20+"vh";s.style.animationDelay=Math.random()*.5+"s";document.body.appendChild(s);setTimeout(()=>s.remove(),2300)}}
function fb(o){tStop();const e=$("fb");e.className="ov on "+o.k;$("fbi").textContent=o.i;$("fbt").textContent=o.t;$("fbp").textContent=o.p||"";$("fbx").innerHTML=o.x||"";$("fbb").textContent=o.b;
 $("fbb").onclick=()=>{e.className="ov";o.cb()};
 $("pbi").style.width=((S.ok+S.fail)/(TF.length+MT.length+MC.length)*100)+"%";if(o.p&&o.p[0]=="+"){const pp=document.createElement("div");pp.className="pp";pp.textContent=o.p;document.body.appendChild(pp);setTimeout(()=>pp.remove(),1500)}
 if(o.k=="ok"){clap();burst(14)}else if(o.k=="half"){good();burst(4)}else bad()}
function award(a){const p=a?5:10;S.sc+=p;S.ps[S.cur]+=p;S.ok++;a?S.h++:S.f++;$("sc").textContent="⭐ "+S.sc;return p}
/* الأنشطة: صح/خطأ + اختيار */
function quiz(list,kind,done){let i=0;
 const go=()=>{if(i>=list.length)return done();const q=list[i];let a=0,fin=false;
  $("stage").innerHTML=`<div class="card"><div class="qn">السؤال ${i+1} من ${list.length}</div><h2>${q.q}</h2><button class="rd" id="rd">🔈 اقرأ السؤال</button><div id="op"></div></div>`;
  $("rd").onclick=()=>say(q.q);const opts=kind=="tf"?[["✅ صح",true],["❌ خطأ",false]]:q.o.map((t,k)=>[["أ","ب","ج"][k]+". "+t,k]);
  const ans=kind=="tf"?(q.a?"صح":"خطأ"):q.o[q.a];
  const res=(ok,to,btn)=>{if(fin)return;tStop();
   if(ok){const p=award(a);fin=true;fb({k:a?"half":"ok",i:a?"🌟":"🎉",t:a?"أحسنت! وصلت للإجابة الصحيحة":"ممتاز! إجابة صحيحة، برافو عليك!",p:"+"+p+" نقاط",x:q.e,b:"التالي ◀",cb:()=>{i++;go()}});return}
   a++;if(btn)btn.disabled=true;
   if(a<2)fb({k:to?"time":"retry",i:to?"⏰":"💭",t:(to?"انتهى الوقت! ":"")+"مش بالضبط! حاول مرة تانية",p:"0 نقاط",x:"عندك محاولة أخيرة.",b:"محاولة ثانية",cb:()=>{tStart(30,()=>res(false,true))}});
   else{fin=true;S.fail++;fb({k:"no",i:"📘",t:"انتهت المحاولات، تعال نتعلم الإجابة الصحيحة",p:"0 نقاط",x:"الإجابة الصحيحة: <b>"+ans+"</b><br>"+q.e,b:"التالي ◀",cb:()=>{i++;go()}})}};
  opts.forEach(([t,v])=>{const b=document.createElement("button");b.className="opt";b.textContent=t;b.onclick=()=>res(v===q.a,false,b);$("op").appendChild(b)});
  tStart(30,()=>res(false,true))};
 go()}
/* نشاط المطابقة */
function match(done){const m=MT.map(()=>({a:0,s:0}));let sel=null,left=MT.length;
 const draw=()=>{$("stage").innerHTML=`<div class="card"><div class="qn">اختر الوسيلة ثم اختر العصر المناسب لها</div><div class="hint" id="mh"></div><div class="cols"><div id="c1"></div><div id="c2"></div></div></div>`;
  MT.forEach((x,i)=>{const b=document.createElement("button");b.className="mc"+(i==sel?" sel":"");b.textContent=x.t;if(m[i].s){b.classList.add("fin");b.style.background=COL[i];b.textContent+=m[i].s==1?" ✓":" ✗";if(m[i].s==2)b.classList.add("x")}b.onclick=()=>{if(!m[i].s){sel=i;draw()}};$("c1").appendChild(b)});
  EO.forEach(j=>{const b=document.createElement("button");b.className="mc era";b.textContent=ER[j];const k=MT.findIndex((x,ii)=>x.e==j&&m[ii].s);if(k>=0){b.classList.add("fin");b.style.background=COL[k];b.textContent+=m[k].s==1?" ✓":" ✗"}else b.onclick=()=>pick(j);$("c2").appendChild(b)})};
 const nxt=()=>{if(left<=0){tStop();done()}else{draw();tRun()}};
 const pick=j=>{if(sel==null){$("mh").textContent="👆 اختر وسيلة النقل أولًا";return}
  const i=sel,x=MT[i];sel=null;
  if(x.e==j){const p=award(m[i].a);m[i].s=1;left--;fb({k:m[i].a?"half":"ok",i:m[i].a?"🌟":"🎉",t:m[i].a?"أحسنت! وصلت للإجابة الصحيحة":"ممتاز! مطابقة صحيحة",p:"+"+p+" نقاط",x:x.t+" ← "+ER[x.e],b:"متابعة ◀",cb:nxt})}
  else{m[i].a++;if(m[i].a<2)fb({k:"retry",i:"💭",t:"مش بالضبط! حاول مرة تانية",p:"0 نقاط",x:"هذه المطابقة غير صحيحة، جرّب عصرًا آخر لهذه الوسيلة.",b:"متابعة ◀",cb:nxt});
   else{m[i].s=2;S.fail++;left--;fb({k:"no",i:"📘",t:"انتهت المحاولات، تعال نتعلم الإجابة الصحيحة",p:"0 نقاط",x:x.t+" ← <b>"+ER[x.e]+"</b>",b:"متابعة ◀",cb:nxt})}}};
 draw();
 tStart(30,()=>{let t="";m.forEach((r,i)=>{if(!r.s){r.s=2;S.fail++;left--;t+=MT[i].t+" ← "+ER[MT[i].e]+"<br>"}});fb({k:"time",i:"⏰",t:"انتهى الوقت! تعال نتعلم الإجابات الصحيحة",p:"0 نقاط",x:t,b:"متابعة ◀",cb:()=>{draw();done()}})})}
/* المعرض */
function hub(){document.body.className="";
 $("hl").innerHTML=HALLS.map(h=>`<div class="hall"><i>${h[0]}</i>${h[1]}</div>`).join("");
 $("hn").textContent="ابدأ المرحلة الأولى ◀";$("hn").onclick=()=>{init();enter(0)};show("s1")}
function enter(n){S.cur=n;document.body.className="h"+n;blip();$("ht").textContent=HALLS[n][0]+" المرحلة "+(n+1);show("s2");
 const end=()=>{S.d[n]=1;cert(n)};
 if(n==0)quiz(TF,"tf",end);else if(n==1)match(end);else quiz(MC,"mc",end)}
const CCSS="@page{size:A4 landscape;margin:0}body{margin:0;font-family:Segoe UI,Tahoma,Arial,sans-serif}#cert{box-sizing:border-box;max-width:1123px;margin:10px auto;padding:clamp(14px,3vw,34px);text-align:center;background:linear-gradient(135deg,#fffbeb,#fef3c7);border:14px double #d97706;border-radius:18px;color:#3b2a14;display:flex;flex-direction:column;justify-content:space-around;gap:10px}#cert .cn{font-size:clamp(1.4rem,4vw,2.4rem)}#cert .ct{font-size:clamp(2rem,7vw,4rem);font-weight:900;color:#c2410c}#cert .cs{font-size:clamp(1rem,2.6vw,1.6rem)}#cert .cm{font-size:clamp(1.8rem,6vw,3.4rem);font-weight:900;color:#0e7490;border-bottom:3px dashed #d97706;display:inline-block;padding:0 20px;align-self:center}#cert .cr{font-size:clamp(1.1rem,3vw,1.9rem);font-weight:800;color:#15803d}#cert .cd{display:flex;justify-content:center;gap:14px;flex-wrap:wrap;font-weight:700;font-size:clamp(.9rem,2.2vw,1.3rem)}#cert.fin{border-color:#7c3aed;background:linear-gradient(135deg,#fdf4ff,#e0f2fe,#fef9c3)}@media print{#cert{width:297mm;max-width:none;height:209mm;margin:0;border-radius:0}}";
{const st=document.createElement("style");st.textContent=CCSS;document.head.appendChild(st)}
const esc=t=>String(t).replace(/[&<>"]/g,c=>({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;"}[c]));
const phr=p=>p>=85?"أداء مبهر! أنت خبير حقيقي في وسائل النقل 🌟":p>=60?"عمل رائع! واصل التقدم وستصبح خبيرًا 👏":"بداية جميلة وشجاعة! بالمحاولة تتحسن دائمًا 💪";
function cert(n){tStop();document.body.className="hf";const fin=n==3,pts=fin?S.sc:S.ps[n],mx=fin?MAX:SM[n],p=Math.round(pts/mx*100);
 let h=`<div class="cn">⭐ 🚂 🚢 🐎 🚝 ⭐</div><div class="ct">شهادة تقدير</div><div class="cs">تُمنح هذه الشهادة إلى البطل</div><div class="cm">${esc(S.n)}</div>`;
 h+=fin?`<div class="cs">لإتمامه لعبة «تطور وسائل النقل في بلادنا»</div><div class="cr">النتيجة النهائية: ${pts} من ${mx} نقطة — نسبة الإنجاز ${p}%</div><div class="cd"><span>🥇 من المحاولة الأولى: ${S.f}</span><span>🥈 من المحاولة الثانية: ${S.h}</span><span>📘 دون إجابة صحيحة: ${S.fail}</span></div>`
 :`<div class="cs">لاجتيازه المرحلة ${["الأولى","الثانية","الثالثة"][n]}: «${SN[n]}»</div><div class="cr">النقاط: ${pts} من ${mx} — نسبة الإنجاز ${p}%</div>`;
 h+=`<div class="cs">${phr(p)}</div>`+(fin?`<div class="cd"><span>📅 تاريخ إتمام اللعبة: ${new Date().toLocaleDateString("ar-EG")}</span></div>`:"")+`<div class="cn">🌟 🚂 🚢 🚝 🌟</div>`;
 const c=$("cert");c.className=fin?"fin":"";c.innerHTML=h;
 const b=$("nx");b.textContent=n<2?"الانتقال إلى المرحلة التالية ◀":n==2?"عرض الشهادة النهائية 🏆":"العب مرة أخرى 🔄";
 b.onclick=()=>{init();if(n<2)enter(n+1);else if(n==2)cert(3);else{reset();hub()}};
 show("s3");if(fin)fan();else good();if(p>0)burst(fin?14:6)}
$("pr").onclick=()=>window.print();
$("dl").onclick=()=>{try{const h='<!DOCTYPE html><html lang="ar" dir="rtl"><head><meta charset="utf-8"><title>شهادة تقدير</title><style>'+CCSS+'</style></head><body>'+$("cert").outerHTML+'</body></html>';const a=document.createElement("a");a.href=URL.createObjectURL(new Blob([h],{type:"text/html"}));a.download="certificate.html";document.body.appendChild(a);a.click();a.remove()}catch(e){window.print()}};
$("go").onclick=()=>{init();const v=$("nm").value.trim();if(!v){$("nh").textContent="من فضلك اكتب اسمك أولًا 😊";return}reset();S.n=v;hub()};
reset();
</script></body></html>
