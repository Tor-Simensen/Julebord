<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Christmas Potluck</title>
<style>
:root{--bg:#fbf6ee;--card:#ffffff;--ink:#2a2420;--mute:#7a6f66;--line:#e8dfd2;--red:#b3261e;--redink:#ffffff;--green:#2f6b4f;--chip:#e3f0e7;--chipink:#1f4d37;--need:#fff1dc;--bar:#e8dfd2;color-scheme:light;box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#181514;--card:#231f1d;--ink:#f1ebe3;--mute:#a99d92;--line:#3a332f;--red:#e5655d;--redink:#1b1210;--green:#6fc29a;--chip:#25382e;--chipink:#bfe8d1;--need:#33281a;--bar:#3a332f;color-scheme:dark}}
:root[data-theme="dark"]{--bg:#181514;--card:#231f1d;--ink:#f1ebe3;--mute:#a99d92;--line:#3a332f;--red:#e5655d;--redink:#1b1210;--green:#6fc29a;--chip:#25382e;--chipink:#bfe8d1;--need:#33281a;--bar:#3a332f;color-scheme:dark}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--ink);font:16px/1.45 -apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,Helvetica,Arial,sans-serif}
main{max-width:720px;margin:0 auto;padding:20px 16px 48px}
h1{font:700 28px/1.15 Georgia,"Times New Roman",serif;margin:0 0 4px}
.sub{color:var(--mute);margin:0 0 16px}
.bar{height:8px;background:var(--bar);border-radius:99px;overflow:hidden;margin:6px 0 4px}
.bar i{display:block;height:100%;background:var(--green);width:0;transition:width .3s}
.stat{font-size:14px;color:var(--mute)}
.me{display:flex;gap:8px;align-items:center;margin:16px 0;flex-wrap:wrap}
.me label{font-weight:600}
input,select{font:inherit;color:var(--ink);background:var(--card);border:1px solid var(--line);border-radius:10px;padding:9px 11px;min-width:0}
input:focus,select:focus,button:focus-visible{outline:2px solid var(--green);outline-offset:1px}
button{font:inherit;cursor:pointer;border-radius:10px;border:1px solid var(--line);background:var(--card);color:var(--ink);padding:8px 12px}
button.pri{background:var(--red);color:var(--redink);border-color:var(--red);font-weight:600}
button.ghost{border-color:transparent;color:var(--mute);padding:8px 6px}
button:disabled{opacity:.55;cursor:default}
.banner{background:var(--need);border:1px solid var(--line);border-radius:10px;padding:10px 12px;margin:12px 0;font-size:14px}
.tools{display:flex;justify-content:space-between;align-items:center;margin:8px 0 0;font-size:14px;color:var(--mute);flex-wrap:wrap;gap:8px}
h2{font:700 13px/1 -apple-system,sans-serif;letter-spacing:.08em;text-transform:uppercase;color:var(--mute);margin:26px 0 10px}
ul{list-style:none;margin:0;padding:0;display:grid;gap:10px}
.item{background:var(--card);border:1px solid var(--line);border-radius:14px;padding:12px 14px}
.item.need{border-left:4px solid var(--red)}
.nm{font-weight:600}
.tag{font-size:12px;color:var(--mute);margin-left:6px}
.chips{display:flex;gap:6px;flex-wrap:wrap;margin:8px 0 0;min-height:26px;align-items:center}
.chip{background:var(--chip);color:var(--chipink);border-radius:99px;padding:3px 6px 3px 11px;font-size:14px;display:inline-flex;align-items:center;gap:2px}
.chip button{border:0;background:none;color:inherit;padding:0 6px;font-size:16px;line-height:1}
.open{color:var(--red);font-size:14px}
.act{display:flex;gap:8px;flex-wrap:wrap;margin-top:10px;align-items:center}
.addp{display:flex;gap:8px;margin-top:10px}
.addp input{flex:1}
.new{margin-top:28px;background:var(--card);border:1px solid var(--line);border-radius:14px;padding:14px}
.new h3{margin:0 0 10px;font-size:16px}
.row{display:flex;gap:8px;flex-wrap:wrap}
.row input{flex:1;min-width:160px}
.chk{display:flex;gap:8px;align-items:center;margin:10px 0 0;font-size:14px}
#toast{position:fixed;left:50%;transform:translateX(-50%);bottom:calc(16px + env(safe-area-inset-bottom,0px));background:var(--ink);color:var(--bg);padding:10px 14px;border-radius:10px;font-size:14px;display:none;max-width:90%}
</style>
</head>
<body>
<main>
  <h1>🎄 Christmas potluck</h1>
  <p class="sub">Pick something to bring, or add your own. Want to team up on a dish? Add a name to it.</p>
  <div class="bar"><i id="fill"></i></div>
  <div class="stat" id="stat">Loading…</div>
  <div id="banner"></div>
  <div class="me"><label for="myname">Your name</label><input id="myname" maxlength="30" placeholder="e.g. Anna"></div>
  <div class="tools"><span id="conn"></span><label><input type="checkbox" id="onlyNeed"> Show only unclaimed</label></div>
  <div id="list"></div>
  <div class="new" id="newbox">
    <h3>Add something that’s not on the list</h3>
    <div class="row">
      <input id="newname" maxlength="60" placeholder="e.g. Lefse, Brownies, Vegan lasagne">
      <select id="newcat"></select>
    </div>
    <label class="chk"><input type="checkbox" id="newclaim" checked> I’m bringing it</label>
    <div class="act"><button class="pri" id="newbtn">Add to list</button></div>
  </div>
</main>
<div id="toast"></div>
<script>
const CATS=["Starters","Mains","Sides","Desserts","Drinks","Other"];
let items=[],db=null,canWrite=true,loaded=false,openAdd=null,confirmDel=null,timer=null;
const $=s=>document.querySelector(s);
const esc=s=>String(s).replace(/[&<>"']/g,c=>({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;"}[c]));
const rid=()=>"b_"+Math.random().toString(36).slice(2,10);
function getName(){try{return localStorage.getItem("pp-name")||""}catch(e){return ""}}
function setName(v){try{localStorage.setItem("pp-name",v)}catch(e){}}
function toast(m){const t=$("#toast");t.textContent=m;t.style.display="block";clearTimeout(toast.t);toast.t=setTimeout(()=>t.style.display="none",3500)}
function bringers(it){const b=it.bringers||{};return Object.keys(b).filter(k=>b[k]).map(k=>({k,n:b[k]}))}
function myName(){return $("#myname").value.trim()}
CATS.forEach(c=>{const o=document.createElement("option");o.textContent=c;$("#newcat").appendChild(o)});
$("#myname").value=getName();
$("#myname").addEventListener("input",e=>setName(e.target.value.trim()));
$("#onlyNeed").addEventListener("change",render);

async function write(fn){
  try{await fn()}catch(e){
    toast(e&&e.code==="invalid_argument"?"You don’t have permission to edit. Ask the host for edit access.":"Couldn’t save. Please try again.");
  }
}
function claim(id){
  const n=myName(); if(!n){toast("Type your name first");$("#myname").focus();return}
  const it=items.find(x=>x.id===id); if(!it)return;
  if(bringers(it).some(b=>b.n.toLowerCase()===n.toLowerCase()))return;
  write(()=>db.doc("items/"+id).update({bringers:{[rid()]:n}}));
}
function addPerson(id){
  const inp=document.querySelector('input[data-k="add-'+id+'"]'); const n=inp?inp.value.trim():""; if(!n)return;
  const it=items.find(x=>x.id===id);
  if(it&&bringers(it).some(b=>b.n.toLowerCase()===n.toLowerCase())){toast(n+" is already on this one");return}
  openAdd=null;
  write(()=>db.doc("items/"+id).update({bringers:{[rid()]:n}}));
}
function removeB(id,k){write(()=>db.doc("items/"+id).update({bringers:{[k]:null}}))}
function delItem(id){
  if(confirmDel!==id){confirmDel=id;render();return}
  confirmDel=null; write(()=>db.doc("items/"+id).delete());
}
$("#newbtn").addEventListener("click",()=>{
  const name=$("#newname").value.trim(); if(!name)return;
  const cat=$("#newcat").value; const n=myName(); const mine=$("#newclaim").checked;
  if(mine&&!n){toast("Type your name first");$("#myname").focus();return}
  const b={}; if(mine)b[rid()]=n;
  $("#newname").value="";
  write(()=>db.collection("items").add({name,cat,custom:true,o:1000,created:Date.now(),bringers:b}));
});
$("#newname").addEventListener("keydown",e=>{if(e.key==="Enter")$("#newbtn").click()});

$("#list").addEventListener("click",e=>{
  const b=e.target.closest("[data-act]"); if(!b)return;
  const a=b.dataset.act,id=b.dataset.id;
  if(a==="claim")claim(id);
  else if(a==="toggle"){openAdd=openAdd===id?null:id;render();const i=document.querySelector('input[data-k="add-'+id+'"]');if(i)i.focus()}
  else if(a==="add")addPerson(id);
  else if(a==="rm")removeB(id,b.dataset.k);
  else if(a==="del")delItem(id);
});
$("#list").addEventListener("keydown",e=>{
  if(e.key==="Enter"&&e.target.dataset.k&&e.target.dataset.k.startsWith("add-"))addPerson(e.target.dataset.k.slice(4));
});

function render(){
  const saved={};document.querySelectorAll("#list input[data-k]").forEach(i=>saved[i.dataset.k]=i.value);
  const fk=document.activeElement&&document.activeElement.dataset?document.activeElement.dataset.k:null;
  const total=items.length,got=items.filter(i=>bringers(i).length).length;
  $("#fill").style.width=total?Math.round(got/total*100)+"%":"0";
  $("#stat").textContent=loaded?(total?got+" of "+total+" items have someone bringing them":"No items yet"):"Loading…";
  $("#banner").innerHTML=canWrite?"":'<div class="banner">You’re viewing this list read-only. Ask the host for edit access to sign up.</div>';
  $("#newbox").style.display=canWrite?"":"none";
  const only=$("#onlyNeed").checked;
  const sorted=items.slice().sort((a,b)=>CATS.indexOf(a.cat)-CATS.indexOf(b.cat)||(a.o||0)-(b.o||0)||(a.created||0)-(b.created||0)||String(a.name).localeCompare(b.name));
  let html="";
  CATS.forEach(c=>{
    const rows=sorted.filter(i=>(CATS.includes(i.cat)?i.cat:"Other")===c&&(!only||!bringers(i).length));
    if(!rows.length)return;
    html+="<h2>"+c+"</h2><ul>";
    rows.forEach(it=>{
      const bs=bringers(it),me=myName().toLowerCase(),mine=me&&bs.some(b=>b.n.toLowerCase()===me);
      html+='<li class="item'+(bs.length?"":" need")+'"><div><span class="nm">'+esc(it.name)+'</span>'+(it.custom?'<span class="tag">added by a guest</span>':"")+'</div>';
      html+='<div class="chips">'+(bs.length?bs.map(b=>'<span class="chip">'+esc(b.n)+(canWrite?'<button data-act="rm" data-id="'+esc(it.id)+'" data-k="'+esc(b.k)+'" aria-label="Remove '+esc(b.n)+'">×</button>':'')+'</span>').join(""):'<span class="open">Nobody yet</span>')+'</div>';
      if(canWrite){
        html+='<div class="act">'+(mine?'<button disabled>✓ You’re bringing this</button>':'<button class="pri" data-act="claim" data-id="'+esc(it.id)+'">I’ll bring this</button>')+
          '<button data-act="toggle" data-id="'+esc(it.id)+'">+ Add a person</button>'+
          '<button class="ghost" data-act="del" data-id="'+esc(it.id)+'">'+(confirmDel===it.id?"Sure? Remove":"🗑 Remove item")+'</button></div>';
        if(openAdd===it.id)html+='<div class="addp"><input data-k="add-'+esc(it.id)+'" maxlength="30" placeholder="Name of co-bringer"><button class="pri" data-act="add" data-id="'+esc(it.id)+'">Add</button></div>';
      }
      html+="</li>";
    });
    html+="</ul>";
  });
  if(loaded&&!html)html='<p class="sub">'+(only?"Everything has someone bringing it. 🎉":"The list is empty.")+'</p>';
  $("#list").innerHTML=html;
  Object.keys(saved).forEach(k=>{const i=document.querySelector('#list input[data-k="'+k+'"]');if(i)i.value=saved[k]});
  if(fk){const i=document.querySelector('#list input[data-k="'+fk+'"]');if(i)i.focus()}
}
render();

(async()=>{
  if(!window.claude||!claude.use){$("#conn").textContent="Open this page from its share link to use it.";return}
  try{
    const user=await claude.use("user");
    if(user){
      const me=await user.me();
      if(!getName()&&me.name){const f=me.name.split(" ")[0];$("#myname").value=f;setName(f)}
      const w=await user.can("data.write"); if(w===false)canWrite=false;
    }
    db=await claude.use("db");
    if(!db){$("#conn").textContent="Sign in to claude.ai to see and edit the list.";canWrite=false;render();return}
    timer=setTimeout(()=>{if(!loaded)$("#conn").textContent="Still connecting…"},10000);
    db.collection("items").onSnapshot(snap=>{
      clearTimeout(timer);loaded=true;$("#conn").textContent="";
      items=snap.docs.map(d=>Object.assign({id:d.id},d.data()));render();
    },e=>{$("#conn").textContent="Couldn’t load the list.";});
  }catch(e){$("#conn").textContent="Couldn’t connect."}
})();
</script>
</body>
</html>
