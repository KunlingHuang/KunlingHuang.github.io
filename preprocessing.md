#  Local genetic correlation analysis between eQTL and GWAS  #

## Data

Date processed: 09/21/2020

Performed local genetic correlation analysis between BrainVar eQTL and ASD GWAS using SUPERGNOVA.

## Input: 
	
	- BrainVar eQTL summary statistics (hg38):

		- Original file obtained from Donna Werling:

			/z/Comp/lu_group/Members/khuang82/Prenatal_postnatal_eQTL/data/BrainVar/091420/cisEqtlRes_allRes_merge_chrAll-181011.txt.gz

			with description file 

			/z/Comp/lu_group/Members/khuang82/Prenatal_postnatal_eQTL/data/BrainVar/091420/eQTLResults_columnKey_SuppTable5.xlsx

		- Chromosome splitted:

			/z/Comp/khuang82/Data/BrainVar/eQTL_by_chr/cisEqtlRes_allRes_merge_chrAll-181011.prenatal_postnatal_only.cleaned_chr.Chr[1..22,X].txt

	
	- ASD GWAS summary statistics

		- Grove et al. (hg19):

			/z/Comp/lu_group/Members/khuang82/Hi-C_GWAS/results/GWAS_sumstat_H-MAGMA_compatible/Grove_ASD_2019.1KG_rsid_update.add_Z.txt
	
		- Huang et al. (hg19): 

			probands: /z/Comp/lu_group/Members/khuang82/Hi-C_GWAS/results/GWAS_sumstat_H-MAGMA_compatible/Huang_ASD_2019.1KG_rsid_update.add_Z.txt

## Processing

Run the script under

`/z/Comp/lu_group/Members/khuang82/Prenatal_postnatal_eQTL/scripts/Preliminary/local_genetic_corr`


* Step 0. Preprocessing eQTL and GWAS. 

	* Step 0-0. The original data is under 

		`/z/Comp/lu_group/Members/khuang82/Prenatal_postnatal_eQTL/data/BrainVar/091420/cisEqtlRes_allRes_merge_chrAll-181011.txt.gz` (compressed)

		`/z/Comp/khuang82/Data/BrainVar/cisEqtlRes_allRes_merge_chrAll-181011.txt` (decompressed)

		Together with the column name descriptions. We trimmed the table since the original file size was too large (35G). We used the script

		`0-0.trim_sumstat_keep_prenatal_postnatal_only.sh`

		to keep the results for prenatal and postnatal eQTL models only (columns 3-19), recode the chromosome information from chrX to X, and split the tables by chromosome. The trimmed tables are saved under

		`/z/Comp/khuang82/Data/BrainVar/eQTL_by_chr`

		containing the eQTL models for chromosome 1-22 and X.


	* Step 0-1. Liftover the BrainVar summary statistics from hg38 to hg19. The output eQTL sumstats are

		`../../../data/BrainVar/091420/eQTL_hg37_liftover_from_hg38/*.txt`


	* Step 0-2. Pool the liftover files together and extract by chromosome again since some of the locations will be mapped to differnt chromosomes.

		
	
	* Step 0-3. Split the eQTL sumstat gene by gene using R script 0-2-split.eQTL.R. The output files are saved as

		`../../../data/BrainVar/091420/eQTL_by_gene_hg37_liftover_from_hg38/chr{1..22}/*.txt`
	

	* Step 0-3. Munge the GWAS and eQTL sumstats.
		
		* Step 0-3-1. Use 

			`/z/Comp/lu_group/Members/khuang82/fusion/ldsc/munge_sumstats.py`

			to QC the ASD GWAS in Grove 2019 and Huang 2019.

		* Step 0-3-2. Modify the QC script to adapt for the eQTL file characteristics. The eQTL files have less SNPs and only strong SNPs in their model, and some genes (84/25148) will have no associations left after QCing.

			* Removed GWAS median P-value check: commented out line 714 and 715 

			* Still printed out an empty file if no SNPs left after QC: 

			*	We added  

					```python
					if(dat_list == []):
        				return dat_list	
					```
					
					to line 302 and 303.
							
			*	We also added
			
			```python
			if len(dat) == 0:
			dat = pd.DataFrame([],columns = ['A1', 'A2', 'SNP', 'Z', 'N'])
			print_colnames = dat.columns
			out_fname = args.out + '.sumstats'
			if args.keep_maf and 'FRQ' in dat.columns:
				print_colnames.append('FRQ')
			if p:
				dat.to_csv(out_fname, sep="\t", index=False,
					columns=print_colnames, float_format='%.3f')
				os.system('gzip -f {F}'.format(F=out_fname))
			return dat
			```

			to line `691-701` to still print out an empty file for the gene which only contains column names.

			The modified script is under `/z/Comp/lu_group/Members/khuang82/fusion/ldsc/munge_sumstats_no_median_check.py`

			
		
					

				




				



