# U.S. Measles Data Repository

The Johns Hopkins University Measles Tracking Team's collection of U.S. measles cases data. For more information about the project, visit the [Bloomberg School of Public Health's Measles Tracker](https://publichealth.jhu.edu/ivac/measles-tracker).

## About the Project

This project is a collaborative, interdisciplinary effort conducted by researchers at Johns Hopkins University who are tracking and modeling the risk of measles in the U.S. The team includes members from multiple JHU divisions:

- **International Vaccine Access Center (IVAC)** - Bloomberg School of Public Health
- **Center for Systems Science and Engineering (CSSE)** - Whiting School of Engineering  
- **Bloomberg Center for Government Excellence** - Johns Hopkins University

**Project Leaders**: Lauren Gardner, Shaun Truelove, and William Moss

## Data Sources

The data are compiled from official sources, including:
- State and county health departments
- Municipal health authorities  
- County-level news releases and verified news articles

All data represents **laboratory-confirmed measles cases** reported by public health authorities in 2025. The complete list of sources is documented in [data_sources_by_state.csv](data_sources_by_state.csv), organized by state.

## Data Files

### 1. `data_sources_by_state.csv`

**Purpose**: Comprehensive documentation of all official sources used to compile measles case data.

| Column | Description |
|--------|-------------|
| `State` | U.S. state name where measles cases were reported |
| `Source_Link` | Direct URL to official health department press release or verified news report |

**Key Features**:
- Multiple source links per state when applicable
- Permanent record of data provenance for transparency
- Essential for data quality assessment and source verification

### 2. `Top_states_time_series.csv`

**Purpose**: Weekly time series for Kansas, New Mexico, and Texas (the three states with highest case counts), organized by epidemiological week and **based on rash onset dates**.

> **Important**: This file uses rash onset dates when available from state health departments, providing epidemiologically accurate timing. As a result, some states-provided time series may not match reporting dates of county-level data.

| Column | Description |
|--------|-------------|
| `week_start` | First day of epidemiological week (YYYY-MM-DD, always Sunday) |
| `week_end` | Last day of epidemiological week (YYYY-MM-DD, always Saturday) |
| `KS_cases` | Weekly count of confirmed cases in Kansas by rash onset date |
| `NM_cases` | Weekly count of confirmed cases in New Mexico by rash onset date |
| `TX_cases` | Weekly count of confirmed cases in Texas by rash onset date |

**Usage Notes**: 
- Designed for epidemiological trend analysis and outbreak curve visualization
- Data may be subject to backward revision as states complete case investigations
- Preferred for transmission modeling due to biological timing accuracy

### 3. `measles_daily_cases_by_county.csv`

**Purpose**: Daily  count of confirmed measles cases by county, providing the most granular temporal and geographic resolution.

| Column | Description |
|--------|-------------|
| `county` | County identifier in "County Name, State Abbreviation" format |
| `fips` | County identifier |
| `2025-01-01` to `[current date]` | Daily case counts (integer values) |

**Key Features**:
- **Reporting date basis**: Reflects when cases were officially reported by health authorities
- **County-level precision**: Enables sub-state geographic analysis
- **Coverage**: All U.S. counties with at least one confirmed case


## Data Dictionary

### Common Standards
- **Date Format**: YYYY-MM-DD (ISO 8601 standard)
- **Case Counts**: Integer values representing laboratory-confirmed measles cases only
- **Geographic Identifiers**: Standardized naming conventions across datasets

### Temporal Data Considerations

| Dataset | Time Basis | Best Use Case |
|---------|------------|---------------|
| County Daily Data | Administrative reporting dates | Public health response timeline, administrative burden tracking |
| State Weekly Data | Epidemiological rash onset dates where available | Epidemiological analysis, outbreak curves, transmission modeling |

### Unusual Cases Methodology:

- The state of Kansas does not provide exact case numbers for counties with less than five confirmed cases. As such, we aggregate such cases to an "unknown county" until further information is available.
- The state of Tennessee provides confirmed case reporting on public health region rather than counties. We provide Tennessee cases on the same level.
- The state of Oklahoma does not provide county information on the confirmed cases. As such, we aggregate all cases to an "Unknown county" until further information is available.
## Update Schedule

Data are updated **Tuesdays and Fridays** at approximately **5:00 PM Eastern Time**.

> **Note**: Historical data is subject to backward revisions as case investigations are completed and additional information becomes available. Previous versions of these data will be maintained through GitHub version-control.

## Terms of Use

This dataset is licensed under the [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/) by Johns Hopkins University on behalf of the JHU Measles Tracking Team.

**Attribution**: Please cite as "JHU Measles Tracking Team Data Repository at Johns Hopkins University" or "JHU Measles Tracking Team Data" for short.

**Copyright**: Johns Hopkins University 2025

## Contact

For general questions or suggestions, please [open a GitHub issue](../../issues) and a member of the team will respond.
*This repository is maintained by the Johns Hopkins University Measles Tracking Team*
