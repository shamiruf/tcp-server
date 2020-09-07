# Úloha č.1 - TCP Server

## Situace

Na planetě Mars bylo vypuštěno několik průzkumných robotů. Roboti posílají informace ze senzorů a fotografie okolí na stacionární družici na oběžné dráze. Nastřádané informace jsou později družicí odeslány k Zemi.

Bohužel však nejsou roboti na povrchu planety sami. Na komunikační server na družici se neustále kdosi pokouší připojovat, prolámat ochrany a server kompromitovat. Nevíme, zda se jedná o konkurenci nebo o cizí formu života, v každém případě je třeba server chránit a striktně dodržovat komunikační protokol.

Implementujte server běžící na družici, který bude od robotů přijímat a ukládat informace.

## Struktura posílaných zpráv

Zprávy poslané klientem

U - uživatelské jméno robota
P - heslo robota
I - informace ze senzorů 
F - fotografie okolí

## Příklad komunikace

kurzíva = text zobrazený v terminálu při spuštění a po ukončení spojení
tučně = server (družice)
normálně = klient (robot)
Sekvence \r\n jsou zobrazeny jako konce řádků.

xsmitka@fray1:/home/zam/xsmitka>telnet baryk-ng.fit.cvut.cz 3999
Trying 147.32.232.173…
Connected to baryk.fit.cvut.cz.
Escape character is '^]'.
200 LOGIN
Robot Emil cislo 33
201 PASSWORD
1645
202 OK
INFO 2014-02-19 03:34 nefunkční čidlo tlaku
202 OK
INFO 2014-02-19 03:35 blíží se jiný robot
202 OK
INFO 2014-02-19 03:38 jiný robot atakován, získáno čidlo tlaku
202 OK
FOTO 3068 …..3068 bytu dat + 4 byty kontrolního součtu…..
202 OK
^]q

telnet> q
Connection closed.
xsmitka@fray1:/home/zam/xsmitka>

Komentář: Spojení se v telnetu ukončí Ctrl+] a potom q a ENTER.

Jiný příklad:

xsmitka@fray1:/home/zam/xsmitka>telnet baryk.fit.cvut.cz 3999
Trying 147.32.232.173…
Connected to baryk.fit.cvut.cz.
Escape character is '^]'.
200 LOGIN
Robot Karel
201 PASSWORD
1045
202 OK
INFO 2014-02-19 03:34 nefunkční čidlo tlaku
202 OK
INFOblablabla
501 SYNTAX ERROR
Connection closed by foreign host.
xsmitka@fray1:/home/zam/xsmitka>
