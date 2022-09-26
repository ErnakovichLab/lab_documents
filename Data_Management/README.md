 # Ernakovich Lab Sequencing Data Management
 ## Why care so much about data management?
 - **Expensive:** Sequencing data is precious and we should keep track of it - think of all the blood, sweat, tears and $$$ that went into getting your data. You wouldn't want to squander it by being careless.
 - **Required by funders:** Most funding agencies data management plans, to be in compliance with those requirements we are responsible for safeguarding our data electronically.
 - **Required for publishing:** Journals require submission of sequencing data to publicly accessible location
 - **Avoids Nagging:** Proper data management now will stop us from hounding you years down the road when you've moved on and never want to hear about your project again.

## Typical data generation workflow

| Step | Examples of Data generated | Management Practice |
| ---- | -------------- | ------------------- |
| Field, laboratory, and other associated experimental data collected prior to or during sequencing.| laboratory notebooks, gas flux outputs, field observations | Compiled into table of inforamtion associated with each sequenced sample; some or all of this data may be deposited with sequencing data. A minimal table associating sample ids to sequencing files *must* be deposited on premise with raw sequencing data. |
| Raw sequencing data received from sequence center. | fastq files R1 and R2 | As soon as you receive data, deposit in in the `/mnt/home/ernakovich/shared/sequencing_data` folder. |
| Data analyzed by you, various products produced | ASV tables, Metagenome Assembled Genomes, Gene tables | Aspects of data necessary to interpreting your analysis should be made publicly available for publication. |
| Paper published off of data | NA | At a minimum, raw sequencing data and associated metadata should be uploaded to the Sequencing read archive. |

## Checklist of data management practices
As soon as you get the sequencing data
- [ ] I have created a folder with the following nameing scheme: `YYYY_MM_DD_ProjectName_PersonInitials` in the `/mnt/home/ernakovich/shared/sequencing_data` directory and deposited my forward and reverse reads into that folder.
- [ ] In addition to the forward and reverse reads, I have uploaded a spreadsheet with sample information to the folder. The spreadsheet contains, at a minimum, the sample ids, their corresponding file names, basic experimental design information.
- [ ] I have uploaded a text file called "methods.txt" that details the laboratory processes that went into generating the sequencing data.

Before publication or before I leave the lab (whichever happens first)
- [ ] I have uploaded my raw reads to SRA
- [ ] I have uploaded any additional sequencing information relevant to the study (Metagenome assembled genomes, functional tables) to the appropriate online archive