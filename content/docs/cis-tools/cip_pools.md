---
title: 'CIP Pools'
weight: 4
---

In der Oettingenstraße 67 stehen den Studierenden der Computerlinguistik spezialisierte Rechnerräume zur Verfügung. Diese sind Sibirien (LU114), Gobi (LU112), Takla-Makan (LU117), Kalahari (BU102), und Antarktis (N001).


## Zugang mit CIP-Kennung
Um die Computer in diesen Räumen nutzen zu können, benötigst du eine sogenannte CIP-Kennung. Die CIP-Kennung wird in der Regel in der ersten Vorlesungswoche vergeben.


## GPU-Nutzung
Ein besonderes Merkmal einiger Rechnerräume ist die Möglichkeit, GPUs (Graphics Processing Units) zu nutzen. Diese spezialisierten Computerchips sind besonders leistungsstark, wenn es darum geht, komplexe grafische Berechnungen durchzüfuhren oder maschinelles Lernen und Deep Learning zu unterstützen. Für Studierende, die in diesen Bereichen arbeiten oder forschen möchten, bietet die GPU-Nutzung immense Vorteile und beschleunigt die Arbeit erheblich.


## Druckerquota
Studierende im Fach Computerlinguistik und Informatik erhalten mit ihrer CIP-Kennung jedes Semester ein Kontingent von 600 kostenfreien Kopien, die an den Druckern in einigen der oben genannten Rechnerräume genutzt werden können. Dieses Kontingent dient dazu, den Druckbedarf fur Studienzwecke abzudecken. 

_Hinweis: das kostenfreie Kopieren ist ausschließlich in den CIP-Räumen und mit deren Druckern möglich. Das Drucken in Bibliotheken kostet entspechend der Preistabellen und ist unberührt von dem kostenfrei nutzbarem Kontingent._


## Fernzugang auf PC's
Die Computerpools der Rechnergruppe können auch remote angesteuert werden. Mit eurer CIP-Kennung, die du am Beginn deines Studiums erhalten hast bzw. erhalten wirst, kannst du dich zunächst über SSH mit dem Netzwerk der Computerpools verbinden. Für den Nutzernamen "Chonksky" latet der Befehl also:
``` bash
ssh chonksky@remote.cip.ifi.lmu.de
```

Nun kannst du nach Belieben den Rechner nutzen. Für Windows-Nutzer ist sicherlich noch das praktische Tool [WinSCP](https://winscp.net/eng/download.php) hilfreich. Mit diesem kannst du dich ebenfalls remote einloggen und dann Dateien von deinem privaten PC auf den Uni-Rechner verschieben und umgekehrt. Ein äquivalentes Produkt für Mac-Nutzende ist [Cyberduck](https://cyberduck.io/).

Praktischerweise sind alle Daten, die auf einem PC des CIP-Pools gespeichert wurden, gleichermaßen auf allen PCs verfügbar. Du musst dir also nicht merken, auf welchem der vielen Rechner mit mehr oder weniger fantasievollen Namen du deine Dateien zurückgelassen hast.

_Um einen Sheduler für die Ausführung deiner Programme zu nutzen, ließ mehr unter SLURM._
