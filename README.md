
<h2>Introduction</h2>
<p>Scopul acestui proiect este de a crea un sistem distribuit care poate rula pe întregul Internet.
Știm că spargerea parolelor este o aplicație complet paralelă.
Constă dintr-un set de operații pe bucăți mici de date. Și, prin urmare, nu trebuie partajate date între diferite noduri de spargere a parolelor pe măsură ce se sparg.
Ei doar primesc o alocare de unitate de lucru, încearcă toate parolele din acea unitate și spun serverului dacă vreuna dintre ele se potrivește.</p>

<h2>Procedure</h2>
<p> Sistemul meu de spargere a parolei este format din două programe, clientul lucrător și serverul.
Serverul creează un job de spargere a parolelor și este responsabil pentru împărțirea jobului în părți și
alocarea acelor părți clienților lucrători.
Clienții și serverul comunică între ei folosind API-ul sockets pentru a trimite pachete UDP.
Aici serverul trimite clientului parola hash reală și un interval.
Clientul după ce se conectează la server primește hash-ul și intervalul și
Încercați să generați toate parolele posibile din interval și să le faceți hash pentru a o compara cu parola hash reală.
Dacă orice hash al parolei generat se potrivește cu hash-ul dat, atunci clientul sparge cu succes parola.
</p>

<h2>Summary</h2>
<p>Când serverul începe să ruleze, generează un hash cu o combinație de parolă aleatoare și dată de sistem. Apoi așteaptă cererea clientului. Clientul a primit un interval de la server. Dacă nu reușește să obțină parola în interval, trimite un pachet RETRY către server. Când un client primește cu succes parola, tipărește parola și, de asemenea, anunță serverul despre aceasta. Dar dacă nu, se încheie cu un mesaj de eșec. </p>
