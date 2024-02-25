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

Bitte beachte, dass du für Python-Programme (und andere Programme mit Ausgaben auf den Bildschirm) die Flag `-u` setzt. Dieses sorgt dafür, dass deine Ausgaben in eine Datei weitergeleitet werden und nicht verloren gehen (weil sie ja normalerweise direkt auf dem Bildschirm angezeigt werden). Natürlich kannst du auch andere Arten von Tools mit SLURM ausführen (etwa `wget` zum Crawling usw.).
Hast du die Datei `script.sh` in dieselbe Directory gelegt, in dem sich dein Programm befindet, kannst du folgendermaßen SLURM starten.

``` bash
sbatch --partition=NvidiaAll script.sh
```

Der Befehl `sbatch` startet dein Programm mithilfe des zuvor angelegten Skripts. Bestätigt wird dies mit einer E-Mail. Interessant ist der Parameter `--partition`. Hiermit gibst du die benötigte Art von Computer an. Das ist wichtig falls du GPUs benötigst. Folgende Partitionen stehen zur Verfügung:

- `All` - alle Rechner ohne besondere Vorgaben zur Hardware/GPU
- `NvidiaAll` - für Jobs, die NVIDIA CUDA als Umgebung brauchen.
- `Nvidia2060`
- `Nvidia1050`
- `AMD`

Weitere Informationen finden sich auf den [Seiten der Rechnerbetriebsgruppe](https://www.rz.ifi.lmu.de/announcements/2022-11-07a_de.html).
Mittels der Anweisung squeue kannst du eine Liste mit allen aktuell laufenden Jobs anzeigen. Darunter befindet sich auch dein Programm. Mit `scancel <YOUR JOB NUMBER>` kannst du deinen Job auch vorzeitig beenden. Deine Jobnummer findest du mit dem Befehl `squeue`.