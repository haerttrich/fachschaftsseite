---
title: 'SLURM'
weight: 5
---

Wie kann man nun aber sicherstellen, dass niemand anderes den PC, auf dem man automatisch eingeloggt wurde, gerade nutzt? Hier kommt ein nützliches Tool namens [SLURM Workload Manager](https://slurm.schedmd.com/documentation.html) (kurz: SLURM) zum Einsatz, das auf den CIP-Rechnern bereits verfügbar ist. Leider ist die Dokumentation von SLURM eher dürftig, sodass wir euch hier ein paar Infos an die Hand geben wollen, die für den alltäglichen Gebrauch von SLURM hilfreich sind.

Zunächst ist es hilfreich, ein Skript zu verwenden, in dem man SLURM mitteilt, mit welchen Optionen die aktuelle Aufgabe durchgeführt werden soll. Legt euch hierzu eine Datei mit bpsw. dem Namen `script.sh` an, die folgendes enthalten muss:

``` bash
#!/bin/bash
#
#SBATCH --job-name=[Kurzname eures Jobs, zum Beispiel --job-name=chonksky-train]
#SBATCH --comment=[Kurze Beschreibung des Jobs, etwa --comment="Training eines NNs"]
#SBATCH --mail-type=ALL
#SBATCH --mail-user=[E-Mail-Adresse, an welche Notifications gehen sollen, etwa wenn der Job beendet, gestartet, oder abgebrochen wurde, zum Beispiel --mail-user=chonksky@campus.lmu.de]
#SBATCH --chdir=[Pfad zum Ordner eurer auszuführenden Datei, etwa --chdir=/home/c/chonksky/Desktop/mein_projekt]
#SBATCH --output=[Wie --chdir, aber mit dem Zusatz slurm.%j.%N.out - auf diese Weise werden die Outputs sauber archiviert. Beispiel: --outputs=/home/c/chonksky/Desktop/mein_projekt/slurm.%j.%N.out]
#SBATCH --ntasks=1

python3 -u mein_programm.py param1 param2
```

Bitte beachtet, dass ihr für Python-Programme (und andere Programme mit Ausgaben auf den Bildschirm) die Flag `-u` setzt. Dieses sorgt dafür, dass eure Ausgaben in eine Datei weitergeleitet werden und nicht verloren gehen (weil sie ja normalerweise direkt auf dem Bildschirm angezeigt werden). Natürlich könnt ihr auch andere Arten von Tools mit SLURM ausführen (etwa `wget` zum Crawling usw.).
Habt ihr euch die Datei `script.sh` in denselben Ordner gelegt, in dem auch euer Programm ist, und ihr auch mit cd dorthin gewechselt seid, seid ihr bereit, SLURM zu starten.

``` bash
sbatch --partition=NvidiaAll script.sh
```

Der Befehl `sbatch` startet euer Programm mithilfe des zuvor angelegten Skripts. Bestätigt wird dies mit einer E-Mail. Interessant ist der Parameter `--partition`. Hier gebt ihr an, welche Art von Computer ihr braucht, insbesondere in Hinblick auf benötigte GPUs. Folgende Partitionen stehen zur Verfügung:

- `All` - alle Rechner ohne besondere Vorgaben zur Hardware/GPU
- `NvidiaAll` - für Jobs, die NVIDIA CUDA als Umgebung brauchen.
- `Nvidia2060`
- `Nvidia1050`
- `AMD`

Weitere Informationen finden sich auf den [Seiten der Rechnerbetriebsgruppe](https://www.rz.ifi.lmu.de/announcements/2022-11-07a_de.html).
Mittels der Anweisung squeue könnt ihr euch eine Liste mit allen aktuell laufenden Jobs anzeigen lassen, wo sich nun auch euer Programm finden sollte. Der Befehl `scancel 12345` beendet euren Job vorzeitig; ersetzt hierzu die `12345` durch die angezeigte Job-Nummer, die ihr mit `squeue` sehen könnt.