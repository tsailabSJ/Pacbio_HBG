# Pacbio_HBG

## Map pacbio


```
minimap2 -t 16 -ax map-hifi --MD --secondary=no \
$genomeFasta \
{{jid}}/${COL2}.fastq \
> {{jid}}/${COL2}/minimap.sam

samtools view -bS minimap.sam > minimap.bam
samtools sort -@ 6 -o minimap.st.bam minimap.bam
samtools index minimap.st.bam
```

## Parse bam

```
python -f minimap.st.bam -o out
```
