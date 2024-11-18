
![](img/pinguin_padawan.png){: style="height:150px;width:150px"; align=right}

* `grep` pour rechercher un motif dans un fichier

```
[tranchant@node10 Bank]$  grep "gene" all.gff3 | head -3 
Chr1	MSU_osa1r7	gene	2903	10817	.	+	.	ID=LOC_Os01g01010;Name=LOC_Os01g01010;Note=TBC%20domain%20containing%20protein%2C%20expressed
Chr1	MSU_osa1r7	gene	11218	12435	.	+	.	ID=LOC_Os01g01019;Name=LOC_Os01g01019;Note=expressed%20protein
Chr1	MSU_osa1r7	gene	12648	15915	.	+	.	ID=LOC_Os01g01030;Name=LOC_Os01g01030;Note=monocopper%20oxidase%2C%20putative%2C%20expressed
```

```
[tranchant@node10 Bank]$  grep "gene" all.gff3 | tail -3 
ChrSy	MSU_osa1r7	mRNA	589676	589999	.	+	.	ID=ChrSy.fgenesh.mRNA.89;Parent=ChrSy.fgenesh.gene.89;Name=ChrSy.fgenesh.mRNA.89
ChrSy	MSU_osa1r7	CDS	589676	589999	11.35	+	0	ID=ChrSy.fgenesh.CDS.327;Parent=ChrSy.fgenesh.mRNA.89;score=11.35
ChrSy	MSU_osa1r7	exon	589676	589999	11.35	+	
```

`grep  -E "gene\s" all.gff3`



Rechercher un motif (pattern) dans une chaine de caractère /MOTIF/

|  | motif recherché | Expresion regulière |
| :-: | :-: | :-: |
| site restriction EcoRI | ATCGCGAATTCAC | /ATCGCGAATTCAC/ |
| site AvaII | GGACC ou GGTCC | /GGACC|GGTCC/ |
| | | /GG[AT]CC/ |
| site restriction BisI | GCNGC | /GC[ACGT]GC/ |

|  | motif recherché | Expresion regulière |
| :-: | :-: | :-: |
| Motif avec une base T présente 3 à n fois | GATC GAAAATTC ... | /A{3,}/ |
| Motif avec une base T présente 0 à 7 fois | GAC GATC GATTC ... | /T{,7}/ |
| Motif présent en début de chaine | AAA... | ^AAA |
| Motif présent en fin de chaine | ...GGG | GGG$ |

`^ATG[ATGC]{30,1000}A{5,10}$`

Expression régulière ou rationnelle = Motif qui décrit un ensemble de chaînes de caractères possibles permettant de faire des sélections

**Communes aux ERs basiques et étendues** :

| | | |
| :-: | :-: | :-: |
| ^ | début de ligne | ^LOC1 |
| $ | fin de ligne | LOC1$ |
| . | n’importe quel caractère | ^L.C1 |
| * | 0 à n fois | ATCA*T |
| [...] | plage de caractères permis | [ATGC] |
| [^...] | plage de caractères interdits | [^ATGC] |
| [0-9] | N’importe quel chiffre | |
| [a-z] | N’importe quelle lettre en minuscule | |
| [^A-Z] | N’importe quel caractère excepté une lettre en majuscule | |
| [a-zA-Z] | N’importe quelle lettre en minuscule ou majuscule | |
| \s |			espace | |
| \t |			tabulation | |
