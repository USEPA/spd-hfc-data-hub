# HFC Data Hub

This repository stores the data used for the HFC Data Hub and Expanded HFC Data tables and charts.

## Git Repository

The repository is organized by year. Each year's data is stored in a separate folder:

```
https://github.com/USEPA/spd-hfc-data-hub/tree/prod/
│
├── 2022_data/
│   ├── Data_Hub_View_....csv
│   └── ...
│
├── 2023_data/
│   ├── Data_Hub_View_....csv
│   └── ...
│
└── 2024_data/
    ├── Data_Hub_View_....csv
    └── ...
```

### CSV Data Upload

Upload the new CSV file to the corresponding year folder, for example:

```
https://github.com/USEPA/spd-hfc-data-hub/tree/prod/2025_data
```

- Maintain **the same CSV structure and formatting** as previous years.
- The first row must contain headers identical to prior datasets. If changes have been made, the JavaScript code will need to be ajusted in Drupal.

---

## Drupal Code

### Clone Existing Page in Drupal

1. In Drupal, locate the current year's pages (i.e., “HFC Data Hub” and "Expanded HFC Data").
2. Use the clone option to duplicate them.
3. Update the cloned pages' titles and URL aliases to reflect the previous year (i.e., "2024 HFC Data Hub" and "2024 Expanded HFC Data").
4. Update the original HFC Data Hub pages as described below.

### JavaScript Code

Ensure that the year_to_use variable has been updated to reflect the year that is to be displayed.

```javascript
const year_to_use = '2025';
```

### Datatable Code

Identify and update the Datatable code block with the following snippet, changing the year to reflect the current year, (e.g., `2025_data`). If columns have changed, the columnsToInclude field will need to be updated.

```javascript
    // HFC Consumption Table
    loadAndInitTable({
        csvUrl: 'https://raw.githubusercontent.com/USEPA/spd-hfc-data-hub/refs/heads/prod/2025_data/Data_Hub_View_Prod_Cons_Table.csv',
        tableSelector: '#production-consumption',
        yearColumnName: 'Year',
        showFooter: true,
        showTotalFooter: true,
        defaultSortCol: 0,
        defaultSortDir: 'asc',
        fixedHeader: false,
        columnsToInclude: ['Chemical', 'Production (MTCO2e)', 'Consumption (MTCO2e)', 'GWP']
    });
```

---

### Highchart Code

Identify and update the Highcharts configuration, changing the year to reflect the current year (e.g., `2025_data`). Ensure each instance of this has been updated.

```javascript
fetch('https://raw.githubusercontent.com/USEPA/spd-hfc-data-hub/refs/heads/prod/2025_data/Data_Hub_View_Prod_Stepdown.csv')
```

---

## Disclaimer


The United States Environmental Protection Agency (EPA) GitHub project code is provided on an "as is" basis and the user assumes responsibility for its use.  EPA has relinquished control of the information and no longer has responsibility to protect the integrity , confidentiality, or availability of the information.  Any reference to specific commercial products, processes, or services by service mark, trademark, manufacturer, or otherwise, does not constitute or imply their endorsement, recommendation or favoring by EPA.  The EPA seal and logo shall not be used in any manner to imply endorsement of any commercial product or activity by EPA or the United States Government.
