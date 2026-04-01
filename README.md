![](https://www.vera.org/dist/img/logo_full.svg)

# ICE Fiscal Year-to-Date (FYTD) Detention Statistics

This repository contains datasets originating from statistical reports published by U.S. Immigration and Customs Enforcement (ICE), archived by Vera and originally published at: U.S. Department of Homeland Security Immigration and Customs Enforcement, “Detention Statistics,”[https://www.ice.gov/detain/detention-management#stats](https://www.ice.gov/detain/detention-management#stats).

The repository includes both the raw files published by ICE and Vera’s cleaned, panel-formatted datasets derived from that data.

Vera has archived ICE’s “biweekly reports” from the above-listed source from September 2020 through present, as well as ICE’s “fiscal year-end reports” for fiscal years (FY) 2019 through 2025. Vera has cleaned, reshaped, and harmonized many of the tables in its archived ICE reports for analysis. Vera’s processed datasets present statistics on the number of people in ICE detention and under ICE’s “Alternatives to Detention” (ATD) monitoring, as reported by ICE since October 2018 (or when each data point was first made available in ICE reports). Vera presents the raw files “as is,” including any inconsistencies or errors present in the data compiled and shared by ICE. This document provides details of the steps Vera took to clean, process, and aggregate the ICE data, shared in Vera’s processed data files. 

Vera intends to update this repository as new reports become available.

# About the Data

Congress has required ICE to publish certain statistics in a publicly available report twice a month, pursuant to requirements established in the Department of Homeland Security (DHS) Appropriations Act of 2020, as amended in 2021 and continued in subsequent spending bills. The reports (which Vera refers to as “the biweekly reports”) include aggregated summary data points such as the number of people detained and under ATD monitoring, the number of people booked into detention, or the number of people booked out of detention by release type.

While these reports offer the most timely glimpse into ICE operations, their format is of limited use for tracking trends over time. The agency overwrites its previous report each time it publishes an updated file, making previous reports no longer available. For many statistics in its reports (such as the current detained population), the longstanding practice of overwriting past reports precludes the public from monitoring how data points change over time. Additionally, each report reflects the current fiscal year-to-date, making it difficult to view numbers across different fiscal years.

Since 2020, Vera has downloaded and archived these reports. Vera researchers have reviewed these files to identify errors and have processed many of the statistics in these reports into the cleaned, panel-formatted data tables available for download in this repository. Vera continues to update these tables regularly as the agency releases more data. 

*The federal fiscal year spans October 1 of the previous year through September 30 of a given year (e.g., FY2025 spans October 1, 2024, to September 30, 2025).

# Directory Tree 
The directory tree below outlines the organization of this repository. This is followed by data dictionaries for each data file.

```
ice-fytd-stats/
    |-- License.md
    |-- README.md
    |-- raw_data/
        |-- FY[YYYY]/
    |-- processed_data/
        |-- exclusions.csv
        |-- current_atd.csv
        |-- current_detained.csv
        |-- fytd_initial_bookins.csv
        |-- fytd_removals.csv
        |-- monthly_detention_summary.csv
        |-- monthly_detention_summary_long.csv
        |-- monthly_final_bookouts.csv
        |-- monthly_final_bookouts_long.csv
        |-- monthly_initial_bookins.csv
        |-- monthly_initial_bookins_long.csv
        
```

# Data Dictionary 

## `raw_data/` 
The folder `raw_data/` contains *all* of Vera's archived copies of ICE reports. Each subfolder `FY[YYYY]/` indicates the fiscal year of the respective file.

Vera has not modified these files in any way, other than the file name. Each report file name includes a prefix Vera added which typically reflects the date when Vera downloaded the file, then the original ICE file name: YYYY-MM-DD_{original ICE file name}.xlsx. For example, the file `raw/FY2026/2026-01-09_FY26_detentionStats01082026.xlsx` contains prefix '2026-01-09_'  added by Vera, followed by 'FY26_detentionStats01082026.xlsx', the original file name from ICE. The date in the prefix is not intended to carry any meaning beyond identifying the raw source file.

Each of the raw files created by ICE contains multiple sheets, including “Detention” and “ATD” sheets presenting multiple tables on numbers of people in detention or under ATD monitoring, as well as a “Footnotes” sheet. **Vera recommends that users review the "Footnotes" tab of the raw files for more detail on how ICE compiled the data.**

Vera found that many of the raw files are entirely or partially unreliable due to apparent errors by ICE, as described in the section below.  **While Vera reviewed and addressed these issues in creating its processed datasets, Vera has not excluded any of its archived files from the raw_data folder.**

## `processed_data/` 

In the `processed_data/` folder, there are 10 cleaned data tables and an `exclusions.csv` file. Each processed data table presents statistics ICE reported over time, taken from one or more tables in the raw file “Detention’ or ‘ATD” sheets, as shown in the table below. Vera notes that ICE’s naming of sheets and tables across the raw files has varied slightly despite presenting the same statistics. For example, the “Detention” sheets in the raw files may be named ‘Detention FY[YY]’, ‘Detention FY[YY] YTD’, or ’Detention EOFY[YYYY]*’.

| Processed Data File | Description | Reported Period | Source Sheet<br>from Raw Files | Source Table Name(s)<br>from Raw Files |
|:---|:---|:---|:---|:---|
| `current_atd.csv` | Number of people currently under ATD monitoring by type of technology and by family unit status.  | Current snapshot as of table_date | ATD | "ATD Active Population Counts and Daily Cost by Technology"; <br><br>"ATD Active Population by Status, Extended Case Management Service, Count and ALIP" |
| `current_detained.csv` | Current number of people in detention by arresting agency, criminal charge/conviction, processing disposition, and family unit status. | Current snapshot as of table_date | Detention |  "ICE Currently Detained by Processing Disposition and Detention Facility Type";<br><br> "ICE Currently Detained by Criminality and Arresting Agency" |
| `fytd_initial_bookins.csv` | The cumulative total number of people ICE booked into detention during the fiscal year by criminal charge/conviction.| Fiscal year-to-date through table_date | Detention | "ICE Initial Book-Ins by Facility Type and Criminality" |
| `fytd_removals.csv` | The cumulative total number of people ICE removed from the United States during the fiscal year by family unit status. | Fiscal year-to-date through table_date | Detention | "ICE Removals" |
| `monthly_detention_summary.csv` | The monthly total number of people ICE booked into and out of detention (initial book-ins, final book-outs), as well as the average daily population (ADP) for each full month. | Monthly | Detention | "ICE Initial Book-Ins by Arresting Agency and Month"; <br><br> "ICE Final Book Outs by Release Reason, Month and Criminality"; <br><br>"ICE Average Daily Population by Arresting Agency, Month and Criminality" |
| `monthly_detention_summary_long.csv` | Formats the wide table `monthly_detention_summary.csv` as long, which additionally includes the minimum and maximum ICE-reported values for each full month.  | "" | "" | "" |
| `monthly_initial_bookins.csv` | The monthly total number of people ICE booked into detention by arresting agency. | Monthly | Detention | "ICE Initial Book-Ins by Arresting Agency and Month" |
| `monthly_initial_bookins_long.csv` | Formats the wide table `monthly_initial_bookins.csv` as long, and additionally includes the minimum and maximum ICE-reported values for each full month. | "" | "" | "" |
| `monthly_final_bookouts.csv` | The monthly total number of people with a final book-out from ICE detention by release reason. | Monthly | Detention | "ICE Final Book Outs by Release Reason, Month and Criminality" |
| `monthly_final_bookouts_long.csv` | Formats the wide table `monthly_final_bookouts.csv` as long, and additionally includes the minimum and maximum ICE-reported values for each full month. | "" | "" | "" |


#### Dates across processed datasets

The processed tables contain date columns described below:

**```file_date```**: Vera uses the field ```file_date``` to indicate the source file within `raw_data/` from which Vera extracted a given data point (as described for each processed table below). The ```file_date``` value is derived from the prefix of the raw file name, which Vera appended to the original ICE file name as described above. **The ```file_date``` field is not intended to carry any meaning beyond identifying the raw source file.**

**```table_date```**: Vera's ```table_date``` field indicates the ICE-reported data extraction date associated with a given source table in the raw files. Because ICE may list different data extraction dates for different tables within the same raw file, **`table_date` does not represent the same value across Vera's processed data tables**, as described for each table below. 

**```year_month```**: There are six processed tables containing monthly statistics that ICE reports for each month within the fiscal year-to-date. The field ```year_month``` reflects the reporting period for each respective statistic (e.g., total initial book-ins of people during a given month, or average daily population during a given month).

**```fiscal_year```**: This field provides the fiscal year indicated by ICE’s original file name for the respective source file. The `fiscal_year` value may differ from the fiscal year associated with the `table_date` value. For example, ICE may release a report after September 30th that pertains to the previous fiscal year.


#### Addressing errors in raw files
As mentioned above, many of the raw files ICE posted on its website are entirely or partially unreliable. For example, there are many instances where ICE failed to update statistics within entire sheets or tables, meaning that the values were wholly duplicated from a previous report. In other instances, ICE did not update the corresponding footnote giving the data extraction date, indicated by duplicate dates across different published files or by dates of a more recent file preceding dates of a previously published file. Sometimes, ICE has posted an updated version of a previously posted file in an apparent effort to correct errors, but without acknowledgement of the update or correction.

In addition, some raw files have duplicate sheets within the file, such as more than one detention sheet or more than one ATD sheet. For example, a sheet "Detention EOFY2020" appears in multiple raw files extracted on the following dates: 2021-01-13, 2021-10-29, 2022-02-17, 2022-08-05, 2022-08-10. This appears to be a mistake, where ICE either failed to rename the sheet to the correct title/fiscal year (in two instances), or included a second "Detention" sheet with the correct name (in three cases). 

Such issues and errors with ICE's reporting have also been documented and discussed by other researchers and even in [government reports](https://www.gao.gov/assets/880/870880.pdf). 

As noted, the folder `raw_data/` contains all of Vera’s archived copies of ICE’s reports, including those with apparent errors. However, for the purpose of generating an accurate panel with one data point per time period for each statistic, as found in the `processed_data/` folder, Vera reviewed the archived files and excluded certain files (or, in some instances, sheets) that contained any errors that made the “Detention” and/or “ATD” sheets unreliable or duplicative. The list of sheets and file dates excluded from processing can be found in `exclusions.csv`. Otherwise, Vera presents the data as it was reported by ICE, except where noted as a Vera-derived variable.

### Current Population Tables
#### `current_atd.csv`
This table presents statistics pulled from the table "ATD Active Population Counts and Daily Cost by Technology", which reports on numbers of people actively under ICE ATD monitoring, disaggregated by type of ATD technology (e.g., SmartLINK, ankle monitor, Veriwatch/wristworn, dual technology, no technology). It also includes data from the table "Case Management Service, Counts and ALIP," which disaggregates the numbers of people on ATDs by family unit status (adults within a family unit or single adults) and whether enrolled in the Extended Case Management Services (ECMS) program, a component of ATD. In this table, ICE classifies families based on Office of Border Patrol (OBP) "apprehensions of adults (18 years old and over) with a [family unit (FAMU)] classification who were subsequently enrolled in ATD."

In the raw data, each of these two tables includes text below the table indicating the date for which the data is applicable. Both tables include a date listed as, "Data from BI Inc. Participants Report, MM.DD.YYYY", which is the same date for both tables. For the "Case Management Service" table only, there is an additional note, "Data from OBP Report, MM.DD.YYYY". Vera chose to use the BI Inc. date for the `table_date` field in `current_atd.csv`, because the OBP date tends to be less recent and updated less frequently than the BI Inc. date (e.g., on a monthly cadence rather than with each new biweekly report), and because the OBP data appears to be used for the purpose of classifying people counted in the tables into family/adult groupings, rather than contributing to the total population counts. 

|Variable                                 |Type      |Description                             |
|:----------------------------------------|:---------|:---------------------------------------|
|`table_date`                               |`date`| The BI Inc. Report date listed below the respective tables in the ATD sheet. The ATD populations in each row should be interpreted as being the current number as of this date.  |
|`fiscal_year`                              |`numeric` | Fiscal year indicated in ICE's original file name. This may differ from the fiscal year associated with the `table_date` value, as mentioned above. |
|`total`                                    |`numeric` | Total number of people enrolled in ICE's ATD monitoring program.|
|`adult`                                    |`numeric` | Number of adults ICE enrolled in its ATD monitoring programs. |
|`ecms_adult`                               |`numeric` | Number of adults ICE enrolled in ECMS, a component of ICE's ATD program.|
|`family`                                   |`numeric` | Number of adults with a family unit ("FAMU") classification whom ICE enrolled in its ATD monitoring program.|
|`ecms_family`                              |`numeric` | Number of adults with a family unit ("FAMU") classification whom ICE enrolled in ECMS, a component of ICE's ATD program. |
|`smartlink`	                              |`numeric` | Number of people enrolled in ATD via ICE's SmartLINK application on a smartphone or tablet using biometric facial identification and GPS capacity.|
|`voiceid`	                              |`numeric` | Number of people with telephonic reporting requirements via phone check-ins with biometric voice matching technology. |
|`wristworn`	                              |`numeric` | Number of people with a wrist-worn GPS tracking device, or "VeriWatch", with facial matching capacity and monitoring location and movement history. |
|`gps`	                                  |`numeric` | Number of people with global position system (GPS) tracking devices. In January 2024, ICE no longer included this column in its reporting, while ICE simultaneously added separate categories for ankle monitors, dual tech, and no tech.|
|`ankle_monitor`                            |`numeric` | Number of people with an ankle-worn GPS tracking device monitoring location and movement history. |
|`dual_tech`	                              |`numeric` | Number of people enrolled in ATD with two or more types of ATD technology. |
|`no_tech`                                  |`numeric` | Number of people enrolled in ATD with required check-ins but no ATD technology. |
|`file_date`                                |`date` | Indicates the source file from which the data was pulled. This date reflects the prefix of the file name in the `raw/` folder. |


#### `current_detained.csv`
This table contains statistics on the currently detained population disaggregated by arresting agency, criminal charge/conviction, and processing disposition, as reported by ICE. These statistics are found within two separate tables in the raw files: "ICE Currently Detained by Processing Disposition and Detention Facility Type" and "ICE Currently Detained by Criminality and Arresting Agency."

|Variable                                 |Type      |Description                             |
|:----------------------------------------|:---------|:---------------------------------------|
|`table_date`                              |`date`   | Date extracted from the "Footnotes" tab of the raw files. This is indicated by "ICE Currently Detained Population Breakdown" in the first column, and in the second column, "ICE National Docket data are a snapshot as of MM/DD/YYYY (IIDS Run Date MM/DD/YYYY; EID as of MM/DD/YYYY)." Vera takes the "EID as of" date to indicate the data extraction date. The detained populations in each row should be interpreted as being the current number as of this date. |
|`fiscal_year`                             |`numeric` | Fiscal year indicated in ICE's original file name for the respective source file. This may differ from the fiscal year associated with the `table_date` value, as mentioned above. |
|`total`                                   |`numeric` | Total number of people currently detained as of `table_date`.  |
|`arresting_agency_ice`                    |`numeric` | Number of people currently detained as of `table_date` who were apprehended by ICE.* |
|`arresting_agency_cbp`                     |`numeric` | Number of people currently detained as of `table_date` who were apprehended by Customs and Border Protection (CBP).** |
|`crim_conviction`                          |`numeric` | Number of people currently detained as of `table_date` whom ICE classifies as having a criminal conviction in the U.S. entered in ICE's data systems at the time of ICE custody. |
|`crim_pending_charge`                      |`numeric` | Number of people currently detained as of `table_date` whom ICE classifies as having a pending criminal charge entered in ICE's data systems at the time of ICE custody. |
|`crim_other`                               |`numeric` | Number of people currently detained as of `table_date` whom ICE classifies as having no criminal convictions or pending charges entered in ICE's data systems at the time of ICE custody.***|
|`processing_disposition_expedited`         |`numeric` | Number of people currently detained as of `table_date` who are subject to expedited removal (I-860). |
|`processing_disposition_nta`               |`numeric` | Number of people currently detained as of `table_date` with a Notice-to-Appear (I-862). |
|`processing_disposition_reinstatement`     |`numeric` | Number of people currently detained as of `table_date` under reinstatement of a prior removal order (I-871). |
|`processing_disposition_other`             |`numeric` | Number of people in immigration detention under another processing disposition.**** |
|`facility_type_frc`                        |`numeric` | Number of people currently detained as of `table_date` in Family Residential Centers (FRC).***** |
|`facility_type_adult`                      |`numeric` | Number of people currently detained as of `table_date` in adult detention facilities. |
|`file_date`                                |`date`    | Indicates the source file from which the data was pulled. This date reflects the prefix of the file name in the `raw/` folder. |

*ICE's footnotes indicate that ICE arrests include: "287(g) Program, Alternatives to Detention, Enforcement and Removal Operations' (ERO) Criminal Alien Program, Detained Docket Control, Detention and Deportation, Law Enforcement Area Response Unit, Mobile Criminal Alien Team, Non-Detained Docket Control, Juvenile, Fugitive Operations, Violent Criminal Alien Section, Joint Criminal Alien Response Team, Probation and Parole, Quick Response Team, User Fee Investigations, Joint Terrorism Task Force, Non-User Fee Investigations, Homeland Security Investigations (HSI) Criminal Arrest Only, and Intelligence."

**ICE's footnotes indicate that CBP arrests include: "Border Patrol, Inspections, Inspections-Air, Inspections- Land, and Inspections- Sea."

*** ICE's footnotes indicate that "Other" may include, but is not limited to: "Non Citizens processed under Administrative Removal, Visa Waiver Program Removal, Stowaway or Crewmember." 

****ICE categorizes the currently detained population into the four processing dispositions as noted in the table above: “Expedited Removal”, “Notice to Appear”, “Reinstatement of Deport Order”, and “Other”. Vera researchers believe that prior to April 2024, ICE included in the “Expedited Removal” category people who withdrew their application for admission in the expedited removal category, and that ICE reclassified this population into “Other” starting in April 2024. This coincides with the U.S. Department of Homeland Security (DHS) Office of Homeland Security Statistics (OHSS) changing its definition of “administrative returns” in April 2024 to include “people who withdrew their application for admission in which expedited removal of immigration proceedings were not considered.” Vera believes this reclassification explains the drop in the currently detained population reported by ICE under the processing disposition “Expedited Removal” and the rise in the detention population under the “Other” processing disposition a few months after this policy shift.

*****Prior to March 2021, ICE used over-72-hour Family Residential Centers (FRCs) to house parents or legal guardians and their children. After March 2021, ICE started using Family Staging Centers (FSCs), an under-72-hour staging program. By December 2021, ICE had stopped housing families. This field may be blank during this time. ICE resumed the use of FRCs on April 7, 2025.

### Fiscal Year-to-Date Tables
#### `fytd_initial_bookins.csv`
This table contains statistics on the initial book-ins to detention, disaggregated by criminal charge/conviction, as reported by ICE. This data is found within the table ‘ICE Initial Book-Ins by Criminality’ of the ‘Detention’ sheet of each raw Excel file, and reflects the initial book-ins of people for the fiscal year-to-date. 

Note that the federal fiscal year begins on October 1st of the previous calendar year (e.g., October 1, 2025, is the first day of FY 2026).

|Variable                                 |Type      |Description                                                    |
|:----------------------------------------|:---------|:--------------------------------------------------------------|
|`table_date`                             |`date`    | Date extracted from the "Footnotes" tab of the raw files. This is indicated by "FY[YYYY] ICE Initial Book-Ins" in the first column, and in the second column, "FY[YYYY] YTD ICE Book-ins data is updated through MM/DD/YYYY (IIDS Run Date MM/DD/YYYY; EID as of MM/DD/YYYY)." Vera takes the "EID as of" date to indicate the data extraction date. The numbers of initial book-ins in each row should be interpreted as the cumulative total for a given `fiscal_year` through this date. |
|`fiscal_year`                            |`numeric` | Fiscal year indicated in ICE's original file name for the respective source file. This may differ from the fiscal year associated with the `table_date` value, as mentioned above. |
|`total`                                  |`numeric` | Total number of people ICE booked into detention for the fiscal year-to-date (October 1st of the previous calendar year through `table_date`). |
|`crim_conviction`                        |`numeric` | Number of people ICE booked into detention with a U.S. criminal conviction in ICE records at time of the enforcement action, for the fiscal year-to-date. |
|`crim_pending_charge`                    |`numeric` | Number of people ICE booked in to immigration detention with pending U.S. criminal charge in ICE records at time of the enforcement action, for the fiscal year-to-date.  |
|`crim_other`                             |`numeric` | Number of people ICE booked into detention with no U.S. criminal convictions or pending charge in ICE records at time of the enforcement action, for the fiscal year-to-date. |
|`delta_total`                            |`numeric` | Vera's derived variable for the change in `fytd_total` since the previous report (within the same fiscal_year). |
|`delta_crim_conviction`                  |`numeric` | Vera's derived variable for the change in `fytd_conviction` since the previous report (within the same `fiscal_year`). |
|`delta_crim_pending_charge`              |`numeric` | Vera's derived variable for the change in `fytd_pending_charge` since the previous report (within the same `fiscal_year`). |
|`delta_crim_other`                       |`numeric` | Vera's derived variable for the change in `fytd_other_book_ins` since the previous report (within the same `fiscal_year`).|
|`delta_n_days`                           |`numeric` | Vera's derived variable for the number of days since the previous report (within the same `fiscal_year`). |
|`file_date`                              |`date`    | Indicates the source file from which the data was pulled. This date reflects the prefix of the file name in the `raw/` folder.  |


#### `fytd_removals.csv`
This table contains the cumulative total number of people ICE removed from the United States during the fiscal year by family unit status. This data includes people who were returned (including voluntary returns, voluntary departures, and withdrawals under docket control), people processed for Expedited Removal, as well as expulsions of people from the United States.
 
|Variable                                 |Type      |Description                             |
|:----------------------------------------|:---------|:---------------------------------------|
|`table_date`                             |`date`    | Date extracted from the "Footnotes" tab of the raw files. This is indicated by "FY[YYYY] ICE Removals" in the first column, and in the second column, "FY[YYYY] YTD ICE Removals data are updated through MM/DD/YYYY (IIDS Run Date MM/DD/YYYY; EID as of MM/DD/YYYY)." Vera takes the "EID as of" date to indicate the data extraction date. The numbers of removals in each row should be interpreted as the cumulative total for a given `fiscal_year` through this date.|
|`fiscal_year`                            |`numeric` | Fiscal year indicated in ICE's original file name for the respective source file. This may differ from the fiscal year associated with the `table_date` value, as mentioned above. |
|`total`                                  |`numeric`| Total number of people ICE removed from the U.S. from the start of the given fiscal year through `table_date`, including returns (voluntary returns, voluntary departures, and withdrawals), expulsions, and expedited removals.* |
|`family`                                 |`numeric`| Number of people ICE removed from the U.S. from the start of the `fiscal_year` through `table_date` whom CBP or ICE reported under "Removals with a FAMU Identifier".|
|`adult`                                  |`numeric`| Vera's derived variable indicating the difference between `total` and `family'. |
|`delta_total`                            |`numeric`| Vera's derived variable for the change in `fytd_total` since the previous report (within the same `fiscal_year`). |
|`delta_family`                           |`numeric`| Vera's derived variable for the change in `fytd_family` since the previous report (within the same `fiscal_year`). |
|`delta_adult`                            |`numeric`| Vera's derived variable for the change in `fytd_adult_removals` since the previous report (within the same `fiscal_year`). |
|`delta_n_days`                           |`numeric`| Vera's derived variable for the number of days since the previous report (within the same `fiscal_year`). |
| `file_date`                             |`date`   | Indicates the source file from which the data was pulled. This date reflects the prefix of the file name in the `raw/` folder. |

*Starting in FY2025, ICE included in these counts people subject to expedited removal or voluntary return who were not detained but who were turned over to ICE for removal. Starting in March 2025, ICE also added people subject to Title 50 Expulsions to removal counts.

### Monthly Tables
Some tables in the raw files are disaggregated by month, such that as the fiscal year progresses ICE populates each month for the fiscal year to date (e.g., “ICE Initial Book-Ins by Arresting Agency and Month”, “ICE Final Book Outs by Release Reason, Month and Criminality”, “ICE Average Daily Population by Arresting Agency, Month and Criminality”). The six processed monthly tables contain statistics ICE reports for each month (indicated by `year_month`) within the fiscal year to-date. Some rows show a partial month (reflected by a gap between `table_date` and the last day of a given `year_month`), typically for the last month of a fiscal year (September) if a year-end report is not available, or the most recent reporting month.

Vera has observed that ICE may retroactively update values from previous months across different raw files. For this reason, Vera provides two versions of the monthly tables, one formatted wide and one formatted long with the minimum and maximum reported values for a each full `year_month`.

As noted above, when creating the processed files, Vera excluded certain files (or in some instances, sheets) that contained errors that made the “Detention” and/or “ATD” sheets unreliable or duplicative. For the six monthly tables, Vera retains data from the most recent of the remaining raw files for any given month (e.g., the latest `table_date` associated with a given `year_month`).

#### `monthly_detention_summary.csv`
This table contains the monthly total number of people ICE booked into and out of detention (initial book-ins, final book-outs), as well as the average daily population (ADP) for a given month. Vera pulled this data from the following tables within the “Detention” sheet of the raw files: “ICE Initial Book-Ins by Arresting Agency and Month”; “ICE Final Book Outs by Release Reason, Month and Criminality”; “ICE Average Daily Population by Arresting Agency, Month and Criminality”. The data in this table is a subset of the data contained in other processed tables (`monthly_initial_bookins`, `monthly_final_bookouts`), with the addition of average daily population (ADP).

|Variable                                 |Type      |Description                             |
|:----------------------------------------|:---------|:---------------------------------------|
|`year_month`                               |`date`    | Reporting month and year (YYYY-MM). For each row, the detention summary statistics should be interpreted as the value for this month. |
|`fiscal_year`                              |`numeric` | Fiscal year indicated in ICE's original file name for the respective source file. This may differ from the fiscal year associated with the `table_date` value, as mentioned above.|
|`initial_bookins`                          |`numeric` | Total number of people ICE booked into detention during the given month (`year_month`).|
|`adp`                                      |`numeric` | Average daily population (ADP), the daily number of people in detention on average during the given month (`year_month`). ICE calculates this statistic based on the daily midnight count, averaged over the number of days in the reporting month.|
|`final_bookouts`                           |`numeric` | Total number of people booked out of ICE custody during the given month (`year_month`). ICE began reporting this data point in FY2024.|
|`final_bookouts_release_to_remove`         |`numeric` | Subset of people booked out of ICE custody during the given month who were booked out due to removal/deportation directly from a detention facility. ICE began reporting this data point in FY2024.|
|`percent_of_final_bookouts_as_removals`    |`numeric` | Vera derived variable of `final_bookouts_release_to_remove` divided by `final_bookouts`, multiplied by 100.|
|`table_date`                               |`date`    | Date extracted from the "Footnotes" tab of the raw files associated with the `adp` field. This is indicated by "FY[YYYY] ICE Average Daily Population and ICE Average Length of Stay" in the first column, and in the second column, "FY[YYYY] YTD ICE Detention data are updated through MM/DD/YYYY (IIDS Run Date MM/DD/YYYY; EID as of MM/DD/YYYY)." Vera takes the "EID as of" date to indicate the data extraction date.|
|`file_date`                                |`date`    | Indicates the source file from which the data was pulled. This date reflects the prefix of the file name in the `raw/` folder.|


#### `monthly_detention_summary_long.csv`
This table formats the wide table `monthly_detention_summary.csv` as long and additionally includes the minimum and maximum ICE-reported values for each full across the raw files. 

|Variable                                 |Type      |Description                             |
|:----------------------------------------|:---------|:---------------------------------------|
|`year_month`                               |`date`    | Reporting month and year (YYYY-MM).  For each row, the detention summary statistics should be interpreted as the total, average, minimum, or maximum for this month. |
|`fiscal_year`                              |`numeric` | Fiscal year indicated in ICE's original file name for the respective source file. This may differ from the fiscal year associated with the `table_date` value, as mentioned above.|
|`variable_name`                            |`text`    | The variable name from the processed table `monthly_detention_summary.csv`: `initial_bookins`, `adp`, `final_bookouts`, `final_bookouts_release_to_remove`.|
|`n`                                        |`numeric` | The value most recently reported by ICE for a given `year_month` across all retained raw files. |
|`min_reported`                             |`numeric` | The minimum value reported by ICE for each full month for a given `year_month` across all retained raw files (after excluding files with errors making the "Detention" and/or "ATD" sheets unreliable; see section above "Addressing Errors in Raw Files"). |
|`max_reported`                             |`numeric` | The maximum value reported by ICE for each full month for a given `year_month` across all retained files. |
|`table_date`                               |`date`    | Date extracted from the "Footnotes" tab of the raw files associated with the variable `adp`. This is indicated by "FY[YYYY] ICE Average Daily Population and ICE Average Length of Stay" in the first column, and in the second column, "FY[YYYY] YTD ICE Detention data are updated through MM/DD/YYYY (IIDS Run Date MM/DD/YYYY; EID as of MM/DD/YYYY)." Vera takes the "EID as of" date to indicate the data extraction date.|
|`file_date`                                |`date`     | Indicates the source file from which the data was pulled. This date reflects the prefix of the file name in the `raw/` folder.|

####  `monthly_initial_bookins.csv`
This table contains the monthly total number of people ICE booked into detention by arresting agency. Vera pulled the data from the “ICE Initial Book-Ins by Arresting Agency and Month” table in the “Detention” tab of the raw files.

|Variable                                   |Type      |Description                             |
|:------------------------------------------|:---------|:---------------------------------------|
|`year_month`                                 |`date`    | Reporting month and year (YYYY-MM). The initial book-in values should be interpreted as the total for this month (or partial month where `table_date` precedes the last day of this month).|
|`fiscal_year`                                |`numeric` | Fiscal year indicated by ICE's original file name for the respective source file. This may differ from the fiscal year associated with the `table_date` value, as mentioned above.
|`total`                                      |`numeric` | Total number of people booked into detention during the given month (`year_month`). |
|`arresting_agency_ice`                                        |`numeric` | Number of people booked into detention who were apprehended by ICE during the given month (`year_month`).|
|`arresting_agency_cbp`                                        |`numeric` | Number of people booked into detention who were apprehended by CBP during the given month (`year_month`).|
|`table_date`                                 |  `date`  | Date extracted from the "Footnotes" tab of the raw files. This is indicated by "FY[YYYY] ICE Initial Book-Ins" in the first column, and in the second column, "FY[YYYY] YTD ICE Book-ins data is updated through MM/DD/YYYY (IIDS Run Date MM/DD/YYYY; EID as of MM/DD/YYYY)." Vera takes the "EID as of" date to indicate the data extraction date.|
|`file_date`                                  |`date`   | Indicates the source file from which the data was pulled. This date reflects the prefix of the file name in the `raw/` folder. | 

####  `monthly_initial_bookins_long.csv`
This table formats the wide table `monthly_initial_bookins.csv` as long and additionally includes the minimum and maximum ICE-reported values for each full month across the raw files. 

|Variable                                   |Type      |Description                             |
|:------------------------------------------|:---------|:---------------------------------------|
|`year_month`                                 |`date`| Reporting month and year (YYYY-MM). The initial book-in values should be interpreted as the total, minimum, or maximum  for this month (or partial month where `table_date` precedes the last day of this month). |
|`fiscal_year`                                |`numeric` | Fiscal year indicated by ICE's original file name for the respective source file. This may differ from the fiscal year associated with the `table_date` value, as mentioned above.
|`variable_name`                              |`text`| The variable name from the processed table `monthly_initial_bookins.csv`: `total`, `arresting_agency_ice`, `arresting_agency_cbp`. |
|`n`                                         |`numeric` | The value most recently reported by ICE for a given `year_month` across all retained raw files. |
|`min_reported`                               |`numeric` | The minimum value reported by ICE for each full month for a given `year_month` across all retained raw files (after excluding files with errors making the "Detention" and/or "ATD" sheets unreliable; see section above "Addressing Errors in Raw Files"). |
|`max_reported`                              |`numeric`| The maximum value reported by ICE for each full month for a given `year_month` across all retained files. |
|`table_date`                                 |`date`| Date extracted from the "Footnotes" tab of the raw files. This is indicated by "FY[YYYY] ICE Initial Book-Ins" in the first column, and in the second column, "FY[YYYY] YTD ICE Book-ins data is updated through MM/DD/YYYY (IIDS Run Date MM/DD/YYYY; EID as of MM/DD/YYYY)." Vera takes the "EID as of" date to indicate the data extraction date. |
|`file_date`                                  |`date`| Indicates the source file from which the data was pulled. This date reflects the prefix of the file name in the `raw/` folder. | 


#### `monthly_final_bookouts.csv`
This table contains the monthly total number of people with a final book-out from ICE detention by release reason. Vera pulled this data from the “ICE Final Book Outs by Release Reason, Month and Criminality” table in the “Detention” tab of the raw files.

In May 2021, ICE began reporting on monthly final releases, disaggregated by release reason. ICE defined "final releases" as book-outs due to the following release reasons: "bonded out", "order of recognizance", "order of supervision", or "paroled." Starting in October 2023, ICE replaced its reporting of final releases with reporting on final book-outs, defined as including the four aforementioned release reasons as well as "proceedings terminated", "release to remove", "relief granted by IJ", "transfer to US Marshals or other agency", "transferred", or "other."

|Variable                                   |Type      |Description                             |
|:------------------------------------------|:---------|:---------------------------------------|
|`year_month`                                 |`date`    | Reporting month and year (YYYY-MM).  The final book-out values should be interpreted as the total for this month (or partial month where `table_date` precedes the last day of this month). |
|`fiscal_year`                                |`numeric` | Fiscal year indicated by ICE's original file name for the respective source file. This may differ from the fiscal year associated with the `table_date` value, as mentioned above. |
|`total_final_bookouts`                       |`numeric` | Total number of people booked out during the given month (`year_month`). |
|`total_final_releases`                       |`numeric` | Number of people booked out during the given month (`year_month`) reflecting an ICE final release reason of "bonded out", "order of recognizance", "order of supervision", or "paroled". This total does not include final book-outs for other reasons such as removal. |
|`bonded_out`                                 |`numeric` | Number of people booked out during the given month (`year_month`) by being bonded out due to decision by either an ICE field office or an immigration judge.|
|`bond_set_by_ice`                            |`numeric` | A subset of `bonded_out`. Number of people booked out during the given month (`year_month`) by being bonded out due to a decision by an ICE field office.|
|`bond_set_by_ij`                             |`numeric` | A subset of `bonded_out`. Number of people booked out during the given month (`year_month`) by being bonded out due to a decision by an immigration judge. |
|`order_of_recognizance`                      |`numeric` | Number of people booked out during the given month (`year_month`) due to an Order of Recognizance while their case is still pending. | 
|`order_of_supervision`                       |`numeric` | Number of people booked out during the given month (`year_month`) due to an Order of Supervision while their case is pending. |
|`paroled`                                    |`numeric` | Number of people booked out during the given month (`year_month`) through humanitarian parole. |
|`proceedings_terminated`                     |`numeric` | Number of people booked out during the given month (`year_month`) due to a termination of immigration proceedings by a decision by an immigration judge or a DHS official. |
|`release_to_remove`                          |`numeric` | Number of people booked out during the given month (`year_month`) due to a removal/deportation directly from a detention facility.|
|`relief_granted_by_ij`                       |`numeric` | Number of people booked out during the given month (`year_month`) due to a disposition of relief granted by an immigration judge.|
|`transfer_to_marshals_or_other_agency`       |`numeric` | Number of people booked out during the given month (`year_month`) to be transferred to the U.S. Marshals Service or another law enforcement agency.|
|`transferred`                                |`numeric` | Number of people with a final book-out reason of transfer during the given month (`year_month`). This does not capture the totality of ICE inter-facility transfers that occur within a detention stay. |
|`other`                                      |`numeric` | Number of people booked out during the given month (`year_month`) due to other reasons. |
|`table_date`                                 |`date`    | Date extracted from the "Footnotes" tab of the raw files. This is indicated by "FY[YYYY] ICE Final Book Outs" in the first column, and in the second column, "FY[YYYY] YTD ICE Final Book Out data are updated through MM/DD/YYYY (IIDS Run Date MM/DD/YYYY; EID as of MM/DD/YYYY)." Vera takes the "EID as of" date to indicate the data extraction date. |
|`file_date`                                  |`date`    | Indicates the source file from which the data was pulled. This date reflects the prefix of the file name in the `raw/` folder. | 


####  `monthly_final_bookouts_long.csv`
This table formats the wide table `monthly_final_bookouts.csv` as long and additionally includes the minimum and maximum ICE-reported values for each full month across the raw files. 


|Variable                                   |Type      |Description                             |
|:------------------------------------------|:---------|:---------------------------------------|
|`year_month`                                 |`date`    | Reporting month and year (YYYY-MM).  The final book-out values should be interpreted as the total, minimum, or maximum  for this month (or partial month where `table_date` precedes the last day of this month). |
|`fiscal_year`                                |`numeric` | Fiscal year indicated by ICE's original file name for the respective source file. This may differ from the fiscal year associated with the `table_date` value, as mentioned above.
|`variable_name`                              |`text`    | The variable name from the processed table `monthly_final_bookouts.csv`: `total_final_bookouts`, `total_final_releases`, `bonded_out`, `bond_set_by_ice`, `bond_set_by_ij`, `order_of_recognizance`, `order_of_supervision`, `paroled`, `proceedings_terminated`, `release_to_remove`, `relief_granted_by_ij`, `transfer_to_marshals_or_other_agency`, `transferred`, and `other`.|
|`n`                                          |`numeric` | The value most recently reported by ICE for a given `year_month` across all retained raw files. |
|`min_reported`                               |`numeric` | The minimum value reported by ICE for each full month for a given `year_month` across all retained raw files. (after excluding files with errors making the "Detention" and/or "ATD" sheets unreliable; see section above "Addressing Errors in Raw Files").|
|`max_reported`                               |`numeric` | The maximum value reported by ICE for each full month for a given `year_month` across all retained files. |
|`table_date`                                 |`date`    |Date extracted from the "Footnotes" tab of the raw files. This is indicated by "FY[YYYY] ICE Final Book Outs" in the first column, and in the second column, "FY[YYYY] YTD ICE Final Book Out data are updated through MM/DD/YYYY (IIDS Run Date MM/DD/YYYY; EID as of MM/DD/YYYY)." Vera takes the "EID as of" date to indicate the data extraction date. 
|`file_date`                                  |`date`    | Indicates the source file from which the data was pulled. This date reflects the prefix of the file name in the `raw/` folder. | 


# Citation

For the Excel files contained the `raw` folder, please cite:


Vera's archive of files from: U.S. Immigration and Customs Enforcement, "Detention Statistics," https://www.ice.gov/detain/detention-management.

For the Excel files contained the `processed_data` folder, please cite:

Vera Institute of Justice, “ICE Fiscal Year-to-Date (FYTD) Detention Statistics,” dataset (New York: Vera Institute of Justice, April 1, 2026), https://github.com/vera-institute/ice-fytd-stats.

# Contributors

This work was a collaborative effort by Neil Agarwal, Bethany Costello, and Noelle Smart.

Vera would like to acknowledge the following colleagues for their support on this project: Jacquelyn Pavilon, Léon Digard, and Nina Siulc.

# Contact
For more information, contact urep@vera.org.
