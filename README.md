<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Tea Account Price Details</title>
<style>
:root{color-scheme:light;--tea:#24533a;--tea2:#397653;--cream:#fffaf0;--ink:#243128;--muted:#69756d;--line:#e4e9e2;--gold:#e5b65b;--page:#f4f6f0;--surface:#ffffff;--field:#ffffff;--field-line:#d7dfd6;--table-head:#fbfcf9;--soft:#edf3ed;--paid-bg:#e5f5e9;--paid-ink:#23683b;--due-bg:#fff0d4;--due-ink:#855b11;--danger-bg:#fff0ef;--danger-ink:#a43c35;--shadow:#203b2710}
:root[data-theme="dark"]{color-scheme:dark;--tea:#9bd3aa;--tea2:#76b889;--ink:#edf4ef;--muted:#a6b4aa;--line:#34443a;--page:#101712;--surface:#19231c;--field:#111a14;--field-line:#405146;--table-head:#202d24;--soft:#26372b;--paid-bg:#183b27;--paid-ink:#a9e6b8;--due-bg:#45351b;--due-ink:#f3d28a;--danger-bg:#472624;--danger-ink:#ffb4ad;--shadow:#00000030}
*{box-sizing:border-box}
body{margin:0;background:var(--page);color:var(--ink);font-family:Arial,Helvetica,sans-serif;transition:background .2s ease,color .2s ease}
header{background:linear-gradient(135deg,#173e2b,#397653);color:#fff;padding:28px 18px 34px}
.wrap{max-width:950px;margin:auto}
.brand{display:flex;align-items:center;gap:13px}
.cup{font-size:35px;background:#ffffff20;border:1px solid #ffffff40;border-radius:15px;padding:10px}
h1{font-size:clamp(24px,5vw,34px);margin:0 0 6px}
header p{margin:0;color:#e5f0e8;font-size:14px}
main{max-width:950px;margin:-17px auto 35px;padding:0 14px}
.stats{display:grid;grid-template-columns:repeat(4,1fr);gap:12px;margin-bottom:17px}
.stat,.panel{background:var(--surface);border:1px solid var(--line);border-radius:16px;padding:17px;box-shadow:0 5px 20px var(--shadow)}
.stat small{display:block;color:var(--muted);font-size:12px;margin-bottom:8px}
.stat strong{font-size:clamp(18px,4vw,25px);color:var(--tea)}
.panel{margin-bottom:15px}
h2{font-size:18px;margin:0 0 15px}
.formgrid{display:grid;grid-template-columns:repeat(4,minmax(0,1fr));gap:12px}
label{display:block;font-size:12px;font-weight:700;color:#526157;margin-bottom:6px}
input,select{width:100%;border:1px solid var(--field-line);border-radius:10px;padding:12px 10px;font-size:15px;background:var(--field);color:var(--ink);min-width:0}
input:focus,select:focus{outline:2px solid #a8cbb1;border-color:var(--tea2)}
.actions{display:flex;gap:10px;flex-wrap:wrap;margin-top:14px}
button{border:0;border-radius:10px;padding:12px 16px;font-weight:700;font-size:14px;cursor:pointer}
.primary{background:var(--tea);color:#fff}.secondary{background:var(--soft);color:var(--tea)}
.tablewrap{overflow-x:auto}
table{width:100%;border-collapse:collapse;min-width:610px}
th,td{text-align:left;padding:12px 10px;border-bottom:1px solid var(--line);font-size:14px}
th{font-size:11px;text-transform:uppercase;letter-spacing:.04em;color:var(--muted);background:var(--table-head)}
td.money{font-weight:700;white-space:nowrap}
.pill{display:inline-block;padding:5px 8px;border-radius:999px;font-size:11px;font-weight:700}
.paid{background:var(--paid-bg);color:var(--paid-ink)}.due{background:var(--due-bg);color:var(--due-ink)}
.del{background:var(--danger-bg);color:var(--danger-ink);padding:7px 9px}
.empty{text-align:center;color:var(--muted);padding:24px}
.headerbar{display:flex;align-items:center;justify-content:space-between;gap:14px;flex-wrap:wrap}
.theme-toggle{background:#ffffff20;color:#fff;border:1px solid #ffffff55;display:inline-flex;align-items:center;gap:8px;white-space:nowrap}
.theme-toggle:focus-visible{outline:3px solid var(--gold);outline-offset:3px}
.foot{font-size:12px;color:var(--muted);text-align:center;margin:18px 0}
@media(max-width:650px){.stats{gap:8px}.stat{padding:12px}.formgrid{grid-template-columns:repeat(2,minmax(0,1fr))}.panel{padding:14px}}
@media(max-width:360px){.stats{grid-template-columns:1fr}.formgrid{grid-template-columns:1fr}}
@media print{body{background:#fff;color:#000}:root{color-scheme:light}header{padding:15px;background:#fff;color:#000}header p{color:#333}main{margin:0 auto}.panel,.stat{box-shadow:none;background:#fff;color:#000}.actions,.delcol,.theme-toggle{display:none}}
</style>
</head>
<body>
<header><div class="wrap headerbar"><div class="brand"><div class="cup">☕</div><div><h1>Tea Account Price Details</h1><p>Tea sales • Daily account • Payment balance</p></div></div><button class="theme-toggle" id="themeToggle" type="button" aria-label="Switch to dark mode" aria-pressed="false"><span id="themeIcon">🌙</span><span id="themeLabel">Dark mode</span></button></div></header>
<main>
  <section class="stats">
    <div class="stat"><small>Total sales</small><strong id="totalSales">₹0.00</strong></div>
    <div class="stat"><small>Total received</small><strong id="totalPaid">₹0.00</strong></div>
    <div class="stat"><small>Balance due</small><strong id="totalDue">₹0.00</strong></div>
    <div class="stat"><small>Total cups sold</small><strong id="totalCups">0 cups</strong></div>
  </section>
  <section class="panel">
    <h2>Add tea account entry</h2>
    <form id="entryForm">
      <div class="formgrid">
        <div><label for="date">Date</label><input id="date" type="date" required></div>
        <div><label for="customer">Customer / Account name</label><input id="customer" placeholder="e.g. Office account" required></div>
        <div><label for="item">Tea type</label><select id="item"><option>Tea</option><option>Milk tea</option><option>Black tea</option><option>Ginger tea</option><option>Coffee</option><option>Other</option></select></div>
        <div><label for="qty">Quantity (cups)</label><input id="qty" type="number" min="1" step="1" value="1" required></div>
        <div><label for="price">Price per cup (₹)</label><input id="price" type="number" min="0" step="0.01" value="12" required></div>
        <div><label for="received">Amount received (₹)</label><input id="received" type="number" min="0" step="0.01" value="0" required></div>
        <div style="grid-column:span 2"><label for="notes">Notes (optional)</label><input id="notes" placeholder="Extra details"></div>
      </div>
      <div class="actions"><button class="primary" type="submit">＋ Add entry</button><button class="secondary" type="reset" id="resetBtn">Clear form</button></div>
    </form>
  </section>
  <section class="panel">
    <h2>Account history</h2>
    <div class="actions" style="margin-top:0;margin-bottom:14px">
      <input id="search" placeholder="Search account name…" aria-label="Search account name" style="max-width:280px">
      <button class="secondary" id="exportBtn" type="button">Export CSV</button>
      <button class="secondary" id="printBtn" type="button">Print account</button>
    </div>
    <div class="tablewrap"><table><thead><tr><th>Date</th><th>Account</th><th>Item</th><th>Qty (cups)</th><th>Total</th><th>Received</th><th>Balance</th><th class="delcol">Action</th></tr></thead><tbody id="rows"></tbody></table></div>
    <div id="empty" class="empty">No entries yet. Add your first tea account above.</div>
  </section>
  <p class="foot">Tea Account Price Details · Sample cup price is ₹12. Change it to your shop’s price. Entries are saved in this browser on this device.</p>
</main>
<script>
const $=id=>document.getElementById(id);
const themeRoot=document.documentElement;
function setTheme(theme){themeRoot.dataset.theme=theme;const dark=theme==='dark';$('themeIcon').textContent=dark?'☀️':'🌙';$('themeLabel').textContent=dark?'Light mode':'Dark mode';$('themeToggle').setAttribute('aria-label',dark?'Switch to light mode':'Switch to dark mode');$('themeToggle').setAttribute('aria-pressed',String(dark));try{localStorage.setItem('teaAccountTheme',theme)}catch(e){}}
let savedTheme='light';try{savedTheme=localStorage.getItem('teaAccountTheme')||'light'}catch(e){}
setTheme(savedTheme==='dark'?'dark':'light');
$('themeToggle').addEventListener('click',()=>setTheme(themeRoot.dataset.theme==='dark'?'light':'dark'));
const fmt=n=>new Intl.NumberFormat('en-IN',{style:'currency',currency:'INR'}).format(n);
const today=new Date(); $('date').value=[today.getFullYear(),String(today.getMonth()+1).padStart(2,'0'),String(today.getDate()).padStart(2,'0')].join('-');
let entries=[];
try{entries=JSON.parse(localStorage.getItem('teaAccountEntries')||'[]')}catch(e){entries=[]}
function save(){try{localStorage.setItem('teaAccountEntries',JSON.stringify(entries))}catch(e){}}
function render(){
 const total=entries.reduce((s,e)=>s+e.qty*e.price,0), paid=entries.reduce((s,e)=>s+e.received,0), due=entries.reduce((s,e)=>s+Math.max(0,e.qty*e.price-e.received),0), cups=entries.reduce((s,e)=>s+e.qty,0);
 $('totalSales').textContent=fmt(total);$('totalPaid').textContent=fmt(paid);$('totalDue').textContent=fmt(due);$('totalCups').textContent=cups+' cups';
 const q=$('search').value.trim().toLowerCase();
 const list=entries.map((e,i)=>({...e,i})).filter(e=>e.customer.toLowerCase().includes(q)).sort((a,b)=>b.date.localeCompare(a.date));
 $('rows').innerHTML=list.map(e=>{const amount=e.qty*e.price,balance=Math.max(0,amount-e.received);return `<tr><td>${esc(e.date)}</td><td><strong>${esc(e.customer)}</strong>${e.notes?`<br><small>${esc(e.notes)}</small>`:''}</td><td>${esc(e.item)}</td><td>${e.qty}</td><td class="money">${fmt(amount)}</td><td>${fmt(e.received)}</td><td><span class="pill ${balance===0?'paid':'due'}">${fmt(balance)}</span></td><td class="delcol"><button class="del" onclick="removeEntry(${e.i})" aria-label="Delete entry">Delete</button></td></tr>`}).join('');
 $('empty').style.display=list.length?'none':'block';
}
function esc(s){return String(s).replace(/[&<>"']/g,c=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c]))}
window.removeEntry=i=>{if(confirm('Delete this account entry?')){entries.splice(i,1);save();render()}};
$('entryForm').addEventListener('submit',e=>{e.preventDefault();const qty=Number($('qty').value),price=Number($('price').value),received=Number($('received').value);if(qty<1||price<0||received<0){alert('Please enter valid amounts.');return}entries.push({date:$('date').value,customer:$('customer').value.trim(),item:$('item').value,qty,price,received,notes:$('notes').value.trim()});save();render();$('customer').value='';$('qty').value='1';$('received').value='0';$('notes').value='';$('customer').focus()});
$('search').addEventListener('input',render);
$('resetBtn').addEventListener('click',()=>setTimeout(()=>{$('date').value=[today.getFullYear(),String(today.getMonth()+1).padStart(2,'0'),String(today.getDate()).padStart(2,'0')].join('-')},0));
$('printBtn').addEventListener('click',()=>window.print());
$('exportBtn').addEventListener('click',()=>{const data=[['Date','Account','Item','Quantity (cups)','Price per cup','Total','Received','Balance','Notes'],...entries.map(e=>[e.date,e.customer,e.item,e.qty,e.price,(e.qty*e.price).toFixed(2),e.received.toFixed(2),Math.max(0,e.qty*e.price-e.received).toFixed(2),e.notes])];const csv=data.map(r=>r.map(v=>'"'+String(v).replace(/"/g,'""')+'"').join(',')).join('\r\n');const a=document.createElement('a');a.href=URL.createObjectURL(new Blob(['\ufeff'+csv],{type:'text/csv;charset=utf-8;'}));a.download='tea-account-price-details.csv';a.click();URL.revokeObjectURL(a.href)});
render();
</script>
</body>
</html>
