# HFGCS EAM Analysis Toolkit

A set suite of Python scripts for analyzing and contextualizing transcriptions of Emergency Action Messages (EAMs) as broadcast by the US military on the HFGCS. This toolkit provides baseline statistical analysis, visualization, pattern detection, and replication analysis capabilities. A sample dataset of transcriptions is provided for testing and to indicate expected format.

## Overview

This toolkit consists of four main analysis scripts designed to work with CSV data containing HFGCS message logs:

- **Character Frequency Analysis** - Statistical analysis of character patterns in messages
- **Traffic Visualization** - Timeline plots and daily traffic charts with prefix grouping
- **Pattern Replication** - Detection of repeating character sequences in messages
- **Pseudo-BLAST Analysis** - Comparative slide analysis to find local alignment patterns between messages

## Details

### Character Frequency Analysis (`eam_characterfreqanalysis_.py`)
- Analyze character frequencies in message content
- Filter out specific digits (0, 1, 8, 9) and problematic characters
- Interactive analysis modes for digits, letters, and character combinations
- Consecutive character detection
- Statistical analysis with outlier detection
- Dark theme visualizations with comprehensive charts

### Traffic Visualization (`eam_linegraph_.py`)
- Timeline scatter plots showing message distribution over time
- Stacked bar charts for daily message counts by prefix
- Intelligent date range processing (short/intermediate/long periods)
- Prefix grouping with color-coded visualization
- Black & white mode for printing compatibility
- Flexible date input formats (YYMMDD, ranges, etc.)

### Pattern Replication (`eam_replicate_.py`)
- Detect repeating character sequences within messages
- Process latest date entries automatically
- Clipboard integration for ad-hoc analysis
- Flexible date-specific analysis
- Robust error handling for various data formats

### Pseudo-BLAST Analysis (`eam_slider_.py`)
- Compare messages using sliding window technique
- Find matching patterns between different messages
- Prefix-based analysis with recent activity tracking
- Configurable offset and minimum match thresholds
- Output results to dated files with detailed alignment information

## Data Format

All scripts expect a CSV file named `SHORTWAVES.csv` with the following columns:

| Column | Description |
|--------|-------------|
| DATE | Date in YYYY.MM.DD format |
| UTC | UTC time in HH:MM format |
| CALLSIGN | Station callsign |
| PR | Message prefix identifier |
| Q | Qualifier _(idiosyncratic, to be documented)_ |
| MESSAGE | Message content |

## Usage

1. Place your `SHORTWAVES.csv` file in the same directory as the scripts
2. Run any script directly.
   
All scripts have fairly robust console instructions and printouts to walk the user through usage.


## Additional Configurations
### `eam_linegraph_.py`
For demonstration purposes, following prefix groups have predefined group assignments:

- **Group 1 (Green)**: YL, YT
- **Group 2 (Orange)**: T5, F6  
- **Group 3 (Yellow)**: [Empty by default]
- **Group 4 (Pink)**: 6K, JC
- **Uncategorized**: All other prefixes

Modify the `PREFIX_GROUPS` dictionary in `eam_linegraph_.py` to customize groupings. _(Note: prefixes may eventually be reused in future years and end up being assigned to different 'groups'; the script as it currently exists cannot handle this.)_
