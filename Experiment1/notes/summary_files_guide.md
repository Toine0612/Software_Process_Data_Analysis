# Summary files guide

- **coverage_pivot_usable_only.csv**
  Wide-format table of usable coverage percentages by project and cycle-time definition. Good for quick comparison and heatmaps.
  Columns: `Project`, `CT1`, `CT2`, `CT3`, `CT4`, `CT5`, `CT6`.

- **coverage_table_usable_only.csv**
  Long-format coverage table with total issues, missing values, non-positive values, usable issues, and coverage percentage for each project × cycle-time definition. This is the main audit table for availability.
  Columns: `Project`, `CT_Definition`, `CT_Column`, `N_total`, `N_missing`, `N_nonpositive`, `N_usable`, `Coverage_pct`.

- **ct_summary_table_usable_only.csv**
  Main descriptive-statistics table for usable cycle times only. Includes median, quartiles, IQR, p10, p90, min, max, mean, and standard deviation for each project × definition.
  Columns: `Project`, `CT_Definition`, `CT_Column`, `N_total`, `N_missing`, `N_nonpositive`, `N_usable`, `Coverage_pct`, `Median_minutes`, `Q1_minutes`, `Q3_minutes`, `IQR_minutes`, `P10_minutes`, `P90_minutes`, `Min_minutes`, `Max_minutes`, `Mean_minutes`, `Std_minutes`, `Median_days`, `Q1_days`, `Q3_days`, `IQR_days`, `P10_days`, `P90_days`, `Min_days`, `Max_days`, `Mean_days`.

- **cycle_time_long_issue_level_usable_only.csv**
  Issue-level long-format file containing only usable observations. Best source for boxplots, violin plots, and other distribution visualizations.
  Columns: `Project_Key`, `Issue_ID`, `Issue_Key`, `Issue_Type`, `Priority`, `Sprint_ID`, `Sprint_Name`, `Story_Point`, `Created`, `Resolution`, `First_In_Progress_Timestamp`, `First_Done_Timestamp`, `Final_Done_Timestamp`, `Was_Reopened`, `CT_Definition`, `CT_Column`, `Cycle_Time_Minutes`, `Usable`.

- **cycle_time_long_issue_level.csv**
  Issue-level long-format file containing all observations plus a `Usable` flag. Useful when you want to inspect exclusions or compare usable vs non-usable issues.
  Columns: `Project_Key`, `Issue_ID`, `Issue_Key`, `Issue_Type`, `Priority`, `Sprint_ID`, `Sprint_Name`, `Story_Point`, `Created`, `Resolution`, `First_In_Progress_Timestamp`, `First_Done_Timestamp`, `Final_Done_Timestamp`, `Was_Reopened`, `CT_Definition`, `CT_Column`, `Cycle_Time_Minutes`, `Usable`.

- **iqr_pivot_days_usable_only.csv**
  Wide-format table of IQR values in days by project and definition. Shows how spread changes across metric definitions.
  Columns: `Project`, `CT1`, `CT2`, `CT3`, `CT4`, `CT5`, `CT6`.

- **median_pivot_days_usable_only.csv**
  Wide-format table of median cycle times in days by project and definition. Shows how the typical value changes across metric definitions.
  Columns: `Project`, `CT1`, `CT2`, `CT3`, `CT4`, `CT5`, `CT6`.

- **project_compare_table_usable_only.csv**
  Compact comparison table with the most useful fields for reporting: missing, non-positive, usable count, coverage, median, IQR, and p10/p90. Good for direct interpretation.
  Columns: `Project`, `CT_Definition`, `N_missing`, `N_nonpositive`, `N_usable`, `Coverage_pct`, `Median_minutes`, `IQR_minutes`, `P10_minutes`, `P90_minutes`, `Median_days`, `IQR_days`, `P10_days`, `P90_days`.

- **usable_pivot.csv**
  Wide-format table of usable issue counts by project and definition. Shows absolute sample size, not just percentages.
  Columns: `Project`, `CT1`, `CT2`, `CT3`, `CT4`, `CT5`, `CT6`.
