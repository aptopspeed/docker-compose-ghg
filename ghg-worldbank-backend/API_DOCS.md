# GHG API Documentation

This document outlines the available endpoints for the Greenhouse Gas (GHG) API. All endpoints are prefixed with `http://localhost:8081/api`.

## Endpoints

### 1. Get All Countries

- **Endpoint:** `/countries`
- **Method:** GET
- **Description:** Retrieves a list of all countries.
- **Example Output:**
  ```json
  [
    {
      "_id": "669cc9854cdf02a2830b6e39",
      "shortName": "BRA",
      "countryName": "Brazil",
      "countryShortName": "BRA"
    }
  ]
  ```

### 2. Get All Sectors

- **Endpoint:** `/sectors`
- **Method:** GET
- **Description:** Retrieves a list of all sectors.
- **Example Output:**
  ```json
  [
    {
      "_id": "669cc9e54cdf02a2830b6e42",
      "shortSector": "agriculture",
      "sectorName": "Agriculture",
      "description": "Agricultural activities"
    }
  ]
  ```

### 3. Get Emissions Trend

- **Endpoint:** `/emissions/trend`
- **Method:** GET
- **Parameters:**
  - `country` (required): Country code (e.g., "IND" for India)
- **Description:** Retrieves the emissions trend for a specific country.
- **Example Output:**
  ```json
  [
    {
      "year": 1990,
      "emissions": {
        "CO2": 22.35,
        "FGas": 1.64,
        "N2O": 2.45,
        "CH4": 0
      },
      "sector": {
        "shortSector": "industry",
        "sectorName": "IndustryProcess"
      }
    }
  ]
  ```

### 4. Get Emissions by Sector

- **Endpoint:** `/emissions/sector`
- **Method:** GET
- **Parameters:**
  - `country` (required): Country code
  - `year` (required): Year of data
- **Description:** Retrieves emissions data by sector for a specific country and year.
- **Example Output:**
  ```json
  [
    {
      "sector": {
        "shortSector": "industry",
        "sectorName": "IndustryProcess"
      },
      "year": 1990,
      "emissions": {
        "CO2": 22.35,
        "FGas": 1.64,
        "N2O": 2.45,
        "CH4": 0
      }
    }
  ]
  ```

### 5. Get Filtered Emissions

- **Endpoint:** `/emissions/filter`
- **Method:** GET
- **Parameters:**
  - `country` (required): Country code
  - `gas` (required): Type of gas (e.g., "N2O")
  - `year` (required): Year of data
- **Description:** Retrieves filtered emissions data for a specific country, gas type, and year.
- **Example Output:**
  ```json
  [
    {
      "emissions": {
        "N2O": 2.45
      },
      "sectorId": {
        "_id": "669cc9e54cdf02a2830b6e43",
        "sectorName": "IndustryProcess"
      }
    },
    {
      "emissions": {
        "N2O": 1.9
      },
      "sectorId": {
        "_id": "669cc9e54cdf02a2830b6e44",
        "sectorName": "Waste"
      }
    },
    {
      "emissions": {
        "N2O": 132.07
      },
      "sectorId": {
        "_id": "669cc9e54cdf02a2830b6e42",
        "sectorName": "Agriculture"
      }
    }
  ]
  ```

### 6. Aggregate Emissions

- **Endpoint:** `/emissions/aggregate`
- **Method:** GET
- **Parameters:**
  - `country` (required): Country code
- **Description:** Retrieves aggregated emissions data for a specific country.
- **Example Output:**
  ```json
  [
    {
      "totalEmissions": 720.4,
      "country": "USA",
      "year": 1990
    },
    {
      "totalEmissions": 708.83,
      "country": "USA",
      "year": 1991
    }
  ]
  ```

### 7. Aggregate Emissions by Country

- **Endpoint:** Not specified in the collection
- **Method:** GET
- **Description:** Aggregates emissions data by country (endpoint details not provided).
- **Example Output:**
  ```json
  [
    {
      "year": 1990,
      "country": "IND",
      "totalEmissions": 616.99
    },
    {
      "year": 1991,
      "country": "IND",
      "totalEmissions": 627.58
    }
  ]
  ```

### 8. Aggregate Emissions by Sector and Year

- **Endpoint:** `/emissions/aggregateSectorbyYear`
- **Method:** GET
- **Parameters:**
  - `year` (required): Year of data
- **Description:** Aggregates emissions data by sector for a specific year.
- **Example Output:**
  ```json
  [
    {
      "country": "Brazil",
      "sector": "Waste",
      "totalEmissions": 30.63
    },
    {
      "country": "China",
      "sector": "Agriculture",
      "totalEmissions": 590.66
    }
  ]
  ```

### 9. Get Distinct Years

- **Endpoint:** `/emissions/years`
- **Method:** GET
- **Description:** Retrieves a list of distinct years available in the emissions data.
- **Example Output:**
  ```json
  [2021, 2020, 2019, 2018]
  ```

### 10. Aggregate Map Data

- **Endpoint:** `/emissions/aggregateMap`
- **Method:** GET
- **Parameters:**
  - `year` (required): Year of data
- **Description:** Aggregates map data for emissions for a specific year.
- **Example Output:**
  ```json
  [
    {
      "totalEmissions": 402.81,
      "countryName": "Brazil",
      "shortName": "BRA"
    },
    {
      "totalEmissions": 913.05,
      "countryName": "China",
      "shortName": "CHN"
    }
  ]
  ```

### 11. Aggregate All Map Data

- **Endpoint:** Not specified in the collection
- **Method:** GET
- **Description:** Aggregates all map data for emissions (endpoint details not provided).
- **Example Output:**
  ```json
  [
    {
      "year": 1990,
      "emissions": 388.5,
      "shortName": "BRA",
      "countryName": "Brazil"
    },
    {
      "year": 1991,
      "emissions": 402.81,
      "shortName": "BRA",
      "countryName": "Brazil"
    }
  ]
  ```

## Notes

- All endpoints use the base URL `http://localhost:8081/api`.
- Some endpoints (7 and 11) are included in the collection but lack specific details. These may be under development or require further configuration.
- Always ensure to provide the required parameters for each endpoint to receive accurate data.
- The example outputs provided are samples and may not reflect the full range of data returned by each endpoint.