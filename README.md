<html lang="fr">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Booléen Lab</title>
<style>
:root{--bg:#f6f7fb;--card:#fff;--tx:#1b1f2a;--mu:#667085;--ac:#4f46e5;--ln:#e3e6ee;--on:#e6f6ec;--ko:#c2410c;--ok:#15803d;
box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media(prefers-color-scheme:dark){:root:not([data-theme=light]){--bg:#0f1220;--card:#181c2e;--tx:#e8eaf3;--mu:#98a2b8;--ac:#8b85ff;--ln:#2a3050;--on:#173324;--ko:#fb923c;--ok:#4ade80}}
:root[data-theme=dark]{--bg:#0f1220;--card:#181c2e;--tx:#e8eaf3;--mu:#98a2b8;--ac:#8b85ff;--ln:#2a3050;--on:#173324;--ko:#fb923c;--ok:#4ade80}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
body{margin:0;background:var(--bg);color:var(--tx);font:16px/1.5 system-ui,-apple-system,"Segoe UI",sans-serif}
.w{max-width:900px;margin:0 auto;padding:18px 16px 40px}
header{display:flex;justify-content:space-between;align-items:center;gap:8px}
h1{margin:0;font-size:1.7rem;letter-spacing:-.5px}h1 span{color:var(--ac)}
.sub{color:var(--mu);margin:2px 0 14px}
.card{background:var(--card);border:1px solid var(--ln);border-radius:14px;padding:14px;margin-bottom:14px}
input{width:100%;box-sizing:border-box;font:1.15rem ui-monospace,Menlo,Consolas,monospace;padding:10px 12px;border:2px solid var(--ln);border-radius:10px;background:var(--bg);color:var(--tx)}
input:focus{outline:none;border-color:var(--ac)}
button{font:inherit;cursor:pointer;border:1px solid var(--ln);background:var(--card);color:var(--tx);border-radius:8px;padding:5px 11px}
button:hover{border-color:var(--ac)}
.row{display:flex;flex-wrap:wrap;gap:6px;margin-top:8px}
.ops button{font-size:1.1rem;min-width:40px}
.chips button{font-size:.85rem;color:var(--mu);border-radius:99px}
#err{color:var(--ko);min-height:1.3em;margin-top:6px;font-size:.92rem}
nav{display:flex;gap:4px;flex-wrap:wrap;margin-bottom:12px}
nav button{border-radius:99px}nav button.a{background:var(--ac);border-color:var(--ac);color:#fff}
section{display:none}section.a{display:block}
.sc{overflow-x:auto}
table{border-collapse:collapse;font-family:ui-monospace,Menlo,Consolas,monospace;margin:0 auto}
th,td{border:1px solid var(--ln);padding:4px 12px;text-align:center}
th{background:var(--bg)}.f{font-weight:700}tr.on td{background:var(--on)}
.kv{margin:8px 0;word-break:break-word}.kv b{color:var(--ac)}
code,.m{font-family:ui-monospace,Menlo,Consolas,monospace}
.big{font-size:1.8rem;text-align:center;margin:10px}
.tag{display:inline-block;padding:2px 10px;border-radius:99px;background:var(--bg);border:1px solid var(--ln);margin:2px;font-family:ui-monospace,monospace;font-size:.9rem}
.tag.s{border-color:var(--ac);color:var(--ac);font-weight:700}
.k td{width:56px;height:46px;font-size:1.1rem}.k th{font-size:.8rem;color:var(--mu)}
.k td.z{color:var(--mu)}.k td.m2{border:2px dashed var(--ac)}
.lg span{display:inline-block;width:14px;height:14px;border-radius:3px;margin-right:6px;vertical-align:middle}
#eo{margin-top:10px;font-weight:600}.ok{color:var(--ok)}.ko{color:var(--ko)}
.laws{display:grid;grid-template-columns:repeat(auto-fill,minmax(230px,1fr));gap:8px;margin-top:12px}
.laws button{text-align:left;padding:8px 10px}.laws small{display:block;color:var(--mu);font-family:ui-monospace,monospace}
.st{border-left:3px solid var(--ac);padding:2px 0 2px 12px;margin:14px 0}.st small,.tag small{color:var(--mu)}.tag small{margin-left:4px}td.e{background:var(--on);font-weight:700;outline:2px solid var(--ac)}summary{cursor:pointer;margin:8px 0}
details{color:var(--mu);font-size:.9rem;margin-top:8px}
</style>
</head>
<body>
<div class="w">
<header><h1>Booléen <span>Lab</span></h1><button id="th" title="Thème">◐</button></header>
<p class="sub">Évaluez, simplifiez et visualisez vos expressions d'algèbre de Boole.</p>

<div class="card">
<input id="f" value=" A + A'B " spellcheck="false" autocomplete="off" aria-label="Expression booléenne">
<div class="row ops" id="ops"></div>
<div class="row chips" id="ch"></div>
<div id="err"></div>
<details><summary>Syntaxe</summary>Variables : A–Z · constantes 0, 1 · NON : ¬ ! ~ ou A' (apostrophe après la variable ou la parenthèse, ex. (A+B)') · ET : ∧ &amp; · * (ou juxtaposition AB) · OU : ∨ + | · XOR : ⊕ ^ · implication : → -&gt; · équivalence : ⇔ &lt;-&gt;. Priorité : NON &gt; ET &gt; XOR &gt; OU &gt; → &gt; ⇔. Jusqu'à 6 variables.</details>
</div>

<nav id="nav"><button data-t="p1" class="a">Table de vérité</button><button data-t="p2">Simplification</button><button data-t="p3">Karnaugh</button><button data-t="p4">Lois &amp; équivalence</button></nav>

<section id="p1" class="a card"></section>
<section id="p2" class="card"></section>
<section id="p3" class="card"></section>
<section id="p4" class="card">
<div class="row" style="margin:0"><input id="e1" value="!(A&B)" style="flex:1;min-width:150px"><input id="e2" value="!A|!B" style="flex:1;min-width:150px"><button id="eb">Comparer</button></div>
<div id="eo"></div>
<div class="laws" id="laws"></div>
</section>
</div>

<script>
const E=id=>document.getElementById(id);
const norm=s=>s.toUpperCase().replace(/<->|<=>|⇔/g,'≡').replace(/->|=>|⇒/g,'→').replace(/[∧&*·.]/g,'&').replace(/[∨+]/g,'|').replace(/[⊕^]/g,'^').replace(/[¬~!]/g,'!');
function parse(src){
 const tk=[...norm(src)].filter(c=>!/\s/.test(c));
 if(!tk.length)throw Error('Saisissez une expression.');
 const bad=tk.find(c=>!/[A-Z01()&|^!≡→']/.test(c));
 if(bad)throw Error('Symbole inconnu : « '+bad+' »');
 let i=0;
 const st=()=>/[A-Z01(!]/.test(tk[i]||'');
 const eqv=()=>{let a=imp();while(tk[i]=='≡'){i++;a={t:'≡',a,b:imp()}}return a};
 const imp=()=>{let a=or();if(tk[i]=='→'){i++;return{t:'→',a,b:imp()}}return a};
 const or=()=>{let a=xor();while(tk[i]=='|'){i++;a={t:'|',a,b:xor()}}return a};
 const xor=()=>{let a=and();while(tk[i]=='^'){i++;a={t:'^',a,b:and()}}return a};
 const and=()=>{let a=not();while(tk[i]=='&'||st()){if(tk[i]=='&')i++;a={t:'&',a,b:not()}}return a};
 const not=()=>{if(tk[i]=='!'){i++;return{t:'!',a:not()}}return atom()};
 const atom=()=>{let a=atom0();while(tk[i]=="'"){i++;a={t:'!',a}}return a};
 const atom0=()=>{const c=tk[i++];
  if(c=='('){const a=eqv();if(tk[i++]!=')')throw Error('Parenthèse fermante manquante.');return a}
  if(c&&/[A-Z]/.test(c))return{t:'v',n:c};
  if(c=='0'||c=='1')return{t:'c',v:+c};
  throw Error('Expression incomplète ou symbole inattendu.')};
 const r=eqv();if(i<tk.length)throw Error('Symbole inattendu : « '+tk[i]+' »');return r}
const ev=(n,e)=>{switch(n.t){case'v':return e[n.n];case'c':return n.v;case'!':return 1-ev(n.a,e)}
 const a=ev(n.a,e),b=ev(n.b,e);
 return n.t=='&'?a&b:n.t=='|'?a|b:n.t=='^'?a^b:n.t=='→'?(1-a)|b:+(a==b)};
const gv=(n,s=new Set)=>{if(n.t=='v')s.add(n.n);else if(n.a){gv(n.a,s);if(n.b)gv(n.b,s)}return s};
const truth=(ast,vs)=>{const r=[],n=vs.length;for(let k=0;k<1<<n;k++){const e={};vs.forEach((v,j)=>e[v]=(k>>(n-1-j))&1);r.push(ev(ast,e))}return r};
const cv=(p,m)=>[...p].every((c,k)=>c=='-'||c==m[k]);
function qm(ms,n){
 const bm=ms.map(m=>m.toString(2).padStart(n,'0'));
 let cur=[...new Set(bm)],pr=[],rounds=[];
 while(cur.length){const used=new Set(),nx=new Set();
  for(let a=0;a<cur.length;a++)for(let b=a+1;b<cur.length;b++){
   let d=-1,c=0;for(let k=0;k<n;k++)if(cur[a][k]!=cur[b][k]){c++;d=k}
   if(c==1){nx.add(cur[a].slice(0,d)+'-'+cur[a].slice(d+1));used.add(cur[a]);used.add(cur[b])}}
  rounds.push({nx:[...nx],un:cur.filter(t=>!used.has(t))});cur.forEach(t=>used.has(t)||pr.push(t));cur=[...nx]}
 const sel=[],rem=new Set(bm);
 bm.forEach(m=>{const c=pr.filter(p=>cv(p,m));if(c.length==1&&!sel.includes(c[0]))sel.push(c[0])});
 const ess=[...sel];sel.forEach(p=>bm.forEach(m=>cv(p,m)&&rem.delete(m)));
 while(rem.size){let best=null,bc=-1;pr.forEach(p=>{const c=[...rem].filter(m=>cv(p,m)).length;if(c>bc){bc=c;best=p}});
  sel.push(best);[...rem].forEach(m=>cv(best,m)&&rem.delete(m))}
 return{pr,sel,ess,rounds,bm:[...new Set(bm)]}}
let S={};
function run(){
 try{const ast=parse(E('f').value),vs=[...gv(ast)].sort();
  if(vs.length>6)throw Error('6 variables maximum.');
  E('err').textContent='';S={vs,res:truth(ast,vs)};table();simp();kmap()}
 catch(x){E('err').textContent=x.message}}
const split=()=>{const mi=[],ma=[];S.res.forEach((r,k)=>(r?mi:ma).push(k));return[mi,ma]};
function table(){
 const{vs,res}=S,n=vs.length,[mi,ma]=split();
 let h='<div class=sc><table><tr>'+vs.map(v=>`<th>${v}</th>`).join('')+'<th class=f>F</th></tr>';
 res.forEach((r,k)=>h+=`<tr class="${r?'on':''}">`+vs.map((v,j)=>`<td>${(k>>(n-1-j))&1}</td>`).join('')+`<td class=f>${r}</td></tr>`);
 h+='</table></div>';
 const kind=!ma.length?'Tautologie':!mi.length?'Contradiction':'Contingente';
 const lit=(k,inv)=>vs.map((v,j)=>((k>>(n-1-j))&1)!=inv?v:'¬'+v);
 const dnf=mi.length?mi.map(k=>lit(k,0).join('·')||'1').join(' + '):'0';
 const cnf=ma.length?ma.map(k=>'('+(lit(k,1).join(' + ')||'0')+')').join('·'):'1';
 h+=`<div class=kv><b>Nature :</b> ${kind}</div><div class=kv><b>Σ minterms :</b> ${mi.length?mi.join(', '):'∅'}</div><div class=kv><b>Π maxterms :</b> ${ma.length?ma.join(', '):'∅'}</div><div class=kv><b>Forme canonique disjonctive :</b> <code>${dnf}</code></div><div class=kv><b>Forme canonique conjonctive :</b> <code>${cnf}</code></div>`;
 E('p1').innerHTML=h}
function simp(){
 const{vs,res}=S,n=vs.length,[mi,ma]=split();
 if(!mi.length||!ma.length){S.cov=[];E('p2').innerHTML=`<p class=big>F = ${mi.length?1:0}</p><p class=sub style="text-align:center">${mi.length?'Tautologie':'Contradiction'}</p>`;return}
 const a=qm(mi,n),b=qm(ma,n);S.cov=a.sel;
 const L=(p,inv)=>[...p].map((c,k)=>c=='-'?null:((c=='1')!=inv?vs[k]:'¬'+vs[k])).filter(Boolean);
 const dnf=a.sel.map(p=>L(p,0).join('·')).join(' + ');
 const cnf=b.sel.map(p=>'('+L(p,1).join(' + ')+')').join('·');
 E('p2').innerHTML=`<div class=kv><b>Somme de produits minimale (Quine–McCluskey)</b></div><p class=big><code>F = ${dnf}</code></p>
 <div class=kv><b>Produit de sommes minimal</b></div><p class=big><code>F = ${cnf}</code></p>
 <div class=kv><b>Implicants premiers :</b> ${a.pr.map(p=>`<span class="tag${a.sel.includes(p)?' s':''}">${L(p,0).join('·')}</span>`).join('')}</div>
 <p class=sub>En surbrillance : implicants retenus dans la couverture minimale.</p>
 <details open><summary><b>Pas à pas : somme de produits</b></summary>${steps(a,vs,0,'minterms de F')}</details>
 <details><summary><b>Pas à pas : produit de sommes</b></summary><p class=sub>Même méthode appliquée aux zéros de F (maxterms) ; les littéraux sont ensuite complémentés.</p>${steps(b,vs,1,'maxterms de F')}</details>`}
function steps(q,vs,inv,lab){
 const L=p=>([...p].map((c,k)=>c=='-'?null:((c=='1')!=inv?vs[k]:'¬'+vs[k])).filter(Boolean).join(inv?' + ':'·'))||(inv?'0':'1');
 const T=p=>`<span class=tag>${p}<small>${L(p)}</small></span>`;
 const G=a=>{const g={};a.forEach(t=>{const k=[...t].filter(c=>c=='1').length;(g[k]=g[k]||[]).push(t)});return Object.keys(g).sort((x,y)=>x-y).map(k=>`<div class=kv><small>${k} bit(s) à 1 :</small> ${g[k].map(T).join('')}</div>`).join('')};
 let h=`<div class=st><b>1. Termes de départ</b> <small>(${lab}, en binaire, groupés par nombre de 1)</small>${G(q.bm)}</div>`;
 q.rounds.forEach((r,i)=>{h+=`<div class=st><b>${i+2}. Fusion n°${i+1}</b> <small>deux termes qui diffèrent d'un seul bit fusionnent (le bit devient –)</small>${r.nx.length?G(r.nx):'<p class=sub>Plus aucune fusion possible.</p>'}${r.un.length?`<div class=kv><small>Non fusionnés → implicants premiers :</small> ${r.un.map(T).join('')}</div>`:''}</div>`});
 const n0=q.rounds.length+2,only=q.bm.map(m=>q.pr.filter(p=>cv(p,m)).length==1);
 let t='<div class=sc><table><tr><th>Implicant</th>'+q.bm.map(b=>`<th>${parseInt(b,2)}</th>`).join('')+'</tr>';
 q.pr.forEach(p=>{t+=`<tr><th style="text-align:left">${L(p)}${q.ess.includes(p)?' ★':''}</th>`+q.bm.map((m,j)=>`<td class="${cv(p,m)&&only[j]?'e':''}">${cv(p,m)?'×':''}</td>`).join('')+'</tr>'});
 t+='</table></div>';
 h+=`<div class=st><b>${n0}. Tableau de couverture</b> <small>× = l'implicant couvre le terme · case encadrée = terme couvert par un seul implicant → ★ essentiel</small>${t}</div>`;
 const ex=q.sel.filter(p=>!q.ess.includes(p));
 h+=`<div class=st><b>${n0+1}. Sélection</b><div class=kv>Essentiels : ${q.ess.map(T).join('')||'aucun'}</div><div class=kv>Ajoutés pour couvrir le reste : ${ex.map(T).join('')||'aucun'}</div><p class=big><code>F = ${inv?q.sel.map(p=>'('+L(p)+')').join('·'):q.sel.map(L).join(' + ')}</code></p></div>`;
 return h}
const gray=k=>{if(!k)return[''];const a=gray(k-1);return[...a.map(x=>'0'+x),...[...a].reverse().map(x=>'1'+x)]};
function kmap(){
 const{vs,res}=S,n=vs.length;
 if(n<2||n>4){E('p3').innerHTML='<p class=sub>Le tableau de Karnaugh gère 2 à 4 variables.</p>';return}
 const rn=n>>1,cn=n-rn,R=gray(rn),C=gray(cn),cov=S.cov||[];
 const pal=['rgba(79,70,229,.28)','rgba(234,88,12,.28)','rgba(22,163,74,.3)','rgba(219,39,119,.28)','rgba(8,145,178,.3)','rgba(202,138,4,.32)'];
 let h=`<div class=sc><table class=k><tr><th>${vs.slice(0,rn).join('')}\\${vs.slice(rn).join('')}</th>`+C.map(c=>`<th>${c}</th>`).join('')+'</tr>';
 R.forEach(r=>{h+=`<tr><th>${r}</th>`;C.forEach(c=>{
  const m=parseInt(r+c,2),b=(r+c),hit=cov.map((p,i)=>cv(p,b)?i:-1).filter(i=>i>=0);
  h+=`<td class="${res[m]?'':'z'}${hit.length>1?' m2':''}" style="${hit.length?'background:'+pal[hit[0]%6]:''}" title="m${m}">${res[m]}</td>`});h+='</tr>'});
 h+='</table></div><p class=lg style="margin-top:12px">'+cov.map((p,i)=>`<span style="background:${pal[i%6]}"></span><code>${[...p].map((c,k)=>c=='-'?'':(c=='1'?vs[k]:'¬'+vs[k])).join('·')}</code>&nbsp;&nbsp; `).join('')+'</p><p class=sub>Les groupes de 1 adjacents (code de Gray, bords reliés) donnent les termes simplifiés.</p>';
 E('p3').innerHTML=h}
function eq(){const o=E('eo');
 try{const a=parse(E('e1').value),b=parse(E('e2').value),vs=[...new Set([...gv(a),...gv(b)])].sort();
  if(vs.length>6)throw Error('6 variables maximum.');
  const x=truth(a,vs),y=truth(b,vs),k=x.findIndex((v,i)=>v!=y[i]),n=vs.length;
  o.className=k<0?'ok':'ko';
  o.textContent=k<0?'✔ Équivalentes : mêmes tables de vérité'+(n?' sur '+vs.join(', '):'')+'.':'✘ Non équivalentes. Contre-exemple : '+vs.map((v,j)=>v+'='+((k>>(n-1-j))&1)).join(', ')+' → '+x[k]+' ≠ '+y[k]}
 catch(e){o.className='ko';o.textContent=e.message}}
const laws=[['De Morgan (ET)','!(A&B)','!A|!B'],['De Morgan (OU)','!(A|B)','!A&!B'],['Distributivité','A&(B|C)','A&B|A&C'],['Absorption','A|(A&B)','A'],['Idempotence','A&A','A'],['Double négation','!!A','A'],['Implication','A→B','!A|B'],['Contraposée','A→B','!B→!A'],['OU exclusif','A^B','A&!B|!A&B'],['Consensus','A&B|!A&C|B&C','A&B|!A&C']];
E('laws').innerHTML=laws.map((l,i)=>`<button data-i="${i}">${l[0]}<small>${l[1]} ≡ ${l[2]}</small></button>`).join('');
E('laws').onclick=e=>{const b=e.target.closest('button');if(!b)return;const l=laws[b.dataset.i];E('e1').value=l[1];E('e2').value=l[2];eq()};
E('eb').onclick=eq;E('e1').oninput=E('e2').oninput=eq;
E('ops').innerHTML=['¬',"'",'∧','∨','⊕','→','⇔','(',')'].map(o=>`<button>${o}</button>`).join('');
E('ops').onclick=e=>{if(e.target.tagName!='BUTTON')return;const f=E('f'),s=f.selectionStart,t=f.selectionEnd;f.setRangeText(e.target.textContent,s,t,'end');f.focus();run()};
const ex=['A→B','(A∨B)∧¬C','A⊕B⊕C','AB + ¬AC + BC','A⇔B','¬(A∧B)∨(C∧D)','A + A·B',"A'B + AB'","(A+B)'"];
E('ch').innerHTML=ex.map(x=>`<button>${x}</button>`).join('');
E('ch').onclick=e=>{if(e.target.tagName=='BUTTON'){E('f').value=e.target.textContent;run()}};
E('nav').onclick=e=>{const t=e.target.dataset.t;if(!t)return;document.querySelectorAll('nav button,section').forEach(x=>x.classList.remove('a'));e.target.classList.add('a');E(t).classList.add('a')};
E('f').oninput=run;
E('th').onclick=()=>{const r=document.documentElement,d=r.dataset.theme?r.dataset.theme=='dark':matchMedia('(prefers-color-scheme:dark)').matches;r.dataset.theme=d?'light':'dark'};
run();eq();
</script>
</body>
</html>
