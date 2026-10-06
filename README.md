# Analisi della produzione di energia nucleare nel mondo

Progetto di analisi dati con Python (pandas, numpy, matplotlib) sul ruolo dell'energia nucleare nel mix elettrico mondiale, basato sul dataset pubblico [Our World in Data - Energy](https://github.com/owid/energy-data).


## Obiettivo

Esplorare come la produzione e la quota di energia nucleare si distribuiscono tra i paesi del mondo, come sono cambiate nel tempo, e se esiste una relazione tra la ricchezza economica di un paese (PIL) e la sua scelta di investire in energia nucleare.

## Dataset

- **Fonte**: [owid/energy-data](https://github.com/owid/energy-data) (CSV `owid-energy-data.csv`)
- **Periodo analizzato**: dal 1950 al 2025 (il nucleare civile nasce a metà anni '50)
- **Pulizia applicata**:
  - Rimossi gli aggregati regionali (World, continenti, unioni economiche) tramite il filtro su `iso_code`, mantenendo solo paesi reali
  - Rimosse le righe senza dati di produzione nucleare (`nuclear_electricity`)

## Struttura del progetto

```
energy-data-analysis/
├── data/
│   └── raw/
│       └── owid-energy-data.csv
├── notebooks/
│   └── Analisi_produzione_nucleare.ipynb
└── README.md
```

## Analisi svolte

1. **Classifica mondiale** dei paesi per produzione nucleare (TWh) nell'anno più recente disponibile
2. **Statistica descrittiva** sulla quota di nucleare nel mix elettrico (`nuclear_share_elec`): media, mediana, deviazione standard, distribuzione (istogramma)
3. **Andamento storico** (1950-2025) della produzione nucleare per un set di paesi selezionati (Francia, USA, Italia, Germania, Cina, Giappone), con lettura degli eventi chiave (referendum italiano 1987, Fukushima 2011, crescita cinese, phase-out tedesco)
4. **Correlazione** tra PIL pro capite e quota nucleare (coefficiente di Pearson)
5. **Correlazione** tra PIL totale e quota nucleare, a confronto con il PIL pro capite

## Principali risultati

- La distribuzione della quota nucleare nel mondo è **fortemente asimmetrica**: la maggior parte dei paesi ha quota zero (mediana = 0%), mentre pochi paesi (su tutti la Francia, ~69%) sono outlier molto distanti dalla media (~8%)
- Né il PIL pro capite (r = 0.23) né il PIL totale (r = 0.13) mostrano una correlazione forte con la quota nucleare
- La scelta di investire in energia nucleare sembra guidata più da **fattori storici, politici e di sicurezza energetica** che dalla sola capacità economica di un paese

## Strumenti utilizzati

- Python 3.11, ambiente conda dedicato (`energy`)
- pandas, numpy, matplotlib
- Jupyter Notebook

## Come riprodurre l'analisi

```bash
conda create -n energy python=3.11 pandas numpy matplotlib jupyter -y
conda activate energy
jupyter notebook
```

Aprire `notebooks/Analisi_produzione_nucleare.ipynb` ed eseguire le celle in ordine.

## Possibili sviluppi futuri

- Estendere il confronto ad altre fonti energetiche (rinnovabili, fossili)
- Analizzare la relazione tra quota nucleare ed emissioni di CO2
- Approfondire il caso dei singoli paesi con serie temporali più dettagliate