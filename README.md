## Part 1: API Documentation


# API Documentation - Recent Posts from Gov Glance API

This README provides details on how to query recent posts from the **Gov Glance API**, specifically for the **Congressional Bills** table within the **United States of America** schema.

## Endpoint

### URL:
```
GET https://api.govglance.org/posts/recent
```

### Query Parameters:

1. **`limit`** *(integer)*: 
   - Specifies the number of records to return.
   - Example: `limit=5` returns 5 records.
   - Default: 20 if not provided.

2. **`skip`** *(integer)*:
   - Skips the specified number of records for pagination.
   - Example: `skip=1` skips the first record.
   - Default: 0 (no records are skipped).

3. **`schema`** *(string)*:
   - Specifies the schema of the data to fetch.
   - Example: `schema=united_states_of_america`.

4. **`table`** *(string)*:
   - Specifies the table to query.
   - Example: `table=congressional_bills`.

5. **`order_by`** *(string)*:
   - Specifies the column by which to order the results.
   - Example: `order_by=action_date`.

6. **`filter_column`** *(string)*:
   - Filters results by the specified column.
   - Example: `filter_column=bill_number`.

7. **`filter_string`** *(string)*:
   - Filters results by the specified value in the `filter_column`.
   - Example: `filter_string=13`.

### Example API Call Without Filters:
```plaintext
https://api.govglance.org/posts/recent?limit=5&skip=1&schema=united_states_of_america&table=congressional_bills&order_by=action_date
```
- **Parameters**:
  - `limit=5`: Limits the results to 5 records.
  - `skip=1`: Skips the first record.
  - `schema=united_states_of_america`: Queries data from the U.S. schema.
  - `table=congressional_bills`: Fetches data from the "congressional_bills" table.
  - `order_by=action_date`: Orders the records by the action date of the bill.

### Example API Call With Filters:
```plaintext
https://api.govglance.org/posts/recent?limit=10&skip=0&schema=united_states_of_america&table=congressional_bills&order_by=action_date&filter_column=bill_number&filter_string=13
```
- **Parameters**:
  - `limit=10`: Limits the results to 10 records.
  - `skip=0`: Does not skip any records (starts from the first record).
  - `schema=united_states_of_america`: Queries data from the U.S. schema.
  - `table=congressional_bills`: Fetches data from the "congressional_bills" table.
  - `order_by=action_date`: Orders the records by the action date of the bill.
  - `filter_column=bill_number`: Filters the results based on the "bill_number" column.
  - `filter_string=13`: Only includes records where the `bill_number` equals "13".

## Example Response Data Format

The response data is returned as a JSON object with the following structure:

```json
 [
    {
      "package_id": "BILLS-119hr3062rh",
      "congress": "119",
      "bill_number": "3062",
      "title": "Promoting Cross-Border Energy Infrastructure Act",
      "long_title": "To Establish A More Uniform, Transparent, And Modern Process To Authorize The Construction, Connection, Operation, And Maintenance Of International Border-Crossing Facilities For The Import And Export Of Oil And Natural Gas And The Transmission Of Electricity.",
      "status": "Placed on the Union Calendar, Calendar No. 151.",
      "action_date": "2025-07-02",
      "url": "https://www.govinfo.gov/app/details/BILLS-119hr3062rh",
      "sponsors": [
        {
          "name": "Ms. Fedorchak",
          "party": "R",
          "state": "ND"
        },
        {
          "name": "Mr. Dunn of Florida",
          "party": "R",
          "state": "FL"
        }
      ]
    },
    {
      "package_id": "BILLS-119hr3898rh",
      "congress": "119",
      "bill_number": "3898",
      "title": "Promoting Efficient Review For Modern Infrastructure Today Act",
      "long_title": "To Amend The Federal Water Pollution Control Act To Make Targeted Reforms With Respect To Waters Of The United States And Other Matters, And For Other Purposes.",
      "status": "Placed on the Union Calendar, Calendar No. 145.",
      "action_date": "2025-07-02",
      "url": "https://www.govinfo.gov/app/details/BILLS-119hr3898rh",
      "sponsors": [
        {
          "name": "Mr. Collins",
          "party": "R",
          "state": "GA"
        },
        {
          "name": "Mr. Graves",
          "party": "R",
          "state": "MO"
        }
      ]
    

```

### Fields:

- **`id`**: Unique identifier for each bill.
- **`bill_number`**: The unique number assigned to each bill.
- **`title`**: The title of the bill.
- **`action_date`**: The date when the bill took action.
- **`summary`**: A brief summary of the bill's contents.
- **`status`**: The current status of the bill (e.g., "Passed", "Pending").

## How API Parameters Affect the Data

### 1. **`limit`**:
   - Determines the number of results returned.
   - Example: Setting `limit=5` will return the first 5 records.

### 2. **`skip`**:
   - Skips a specified number of records for pagination.
   - Example: Setting `skip=1` skips the first record, effectively starting from the second.

### 3. **`filter_column` & `filter_string`**:
   - These parameters allow filtering the data based on a column and value.
   - Example: Setting `filter_column=bill_number&filter_string=13` will return only records where the `bill_number` is "13".

### 4. **`order_by`**:
   - Specifies the column by which to order the data.
   - Example: Setting `order_by=action_date` orders the records by their `action_date`.

## Conclusion

This API provides a flexible way to retrieve, filter, and paginate through data for U.S. Congressional Bills. By adjusting the `limit`, `skip`, `filter_column`, `filter_string`, and `order_by` parameters, you can tailor the API response to your needs.


---

## Part 2: Project README


# API Feed Example

This is a simple React app that demonstrates how to use the provided API to fetch and display feed data, specifically Congressional Bills, in a styled, user-friendly interface. The data is fetched using a custom hook (`useFeedData`), and displayed with Bootstrap components for a clean, responsive UI.

## Features

- Fetches and displays a list of recent Congressional bills from the API.
- Displays 25 items per section by default.
- Uses Bootstrap cards to present each bill's information.
- Provides a "More Details" button that redirects to the detailed bill page.

## Tech Stack

- **React**: A JavaScript library for building user interfaces.
- **React Bootstrap**: A library that provides Bootstrap components as React components.
- **Custom Hooks**: A React hook (`useFeedData`) to handle API calls and data fetching.


## Installation

### 1. Clone the repository

Clone this repository to your local machine.

```bash
git clone https://github.com/your-username/api-feed-example.git
```

### 2. Navigate to the project directory

```bash
cd api-feed-example
```

### 3. Install dependencies

Install the necessary dependencies for the app.

```bash
npm install
```

### 4. Run the development server

Start the app in development mode.

```bash
npm start
```

The app will be available at `http://localhost:3000` in your browser.

## Folder Structure

```
api-feed-example/
├── public/
│   ├── index.html
│   └── ...
├── src/
│   ├── App.js                # Main application component
│   ├── hooks/
│   │   └── useFeedData.js     # Custom hook for fetching API data
│   ├── components/
│   │   └── FeedSection.js     # Component for displaying feed data
│   ├── App.css                # Custom CSS file
│   └── index.js               # Entry point for the React app
├── package.json               # Project metadata and dependencies
└── README.md                  # Project documentation
```

## Usage

### App Component

The `App.js` file is the main entry point of the app. It displays the `FeedSection` component, which fetches and renders the feed data from the provided API URL.

```jsx
import React from 'react';
import FeedSection from './components/FeedSection';

const App = () => {
  return (
    <div className="p-5">
      <h1 className="text-center mb-4 app-title">API Feed Example</h1>
      {/* FeedSection component that fetches data from the API */}
      <FeedSection
        title="Recent Congressional Bills"
        apiEndpoint="https://api.govglance.org/posts/recent?limit=25&schema=united_states_of_america&table=congressional_bills&order_by=action_date&skip=0"  // Full API URL
      />
    </div>
  );
};

export default App;
```

### FeedSection Component

The `FeedSection` component is responsible for fetching data using the custom hook and rendering the feed content.

- **Props:**
  - `title`: The title of the feed section (e.g., "Recent Congressional Bills").
  - `apiEndpoint`: The full API endpoint URL to fetch data from (passed directly in the component).

- **Data Display:**
  - The component uses the `useFeedData` hook to fetch the latest 25 items.
  - Each item is rendered inside a Bootstrap card.
  - The bill's title, status, bill number, chamber, committee, and description are displayed.
  - A "More Details" button is provided to view additional information on the bill's official page.

```jsx
import { Spinner, Card, Button, Container, Row, Col } from 'react-bootstrap';
import useFeedData from './hooks/useFeedData';  // Import custom hook
import './App.css';  // Import custom styles

const FeedSection = ({ title, apiEndpoint }) => {
  const { data, loading, error } = useFeedData(apiEndpoint, 25); // Fetch 25 items

  // Loading state
  if (loading) {
    return (
      <div className="text-center">
        <h4>{title}</h4>
        <Spinner animation="border" />
      </div>
    );
  }

  // Error state
  if (error) {
    return (
      <div className="text-center">
        <h4>{title}</h4>
        <div className="text-danger">{`Error: ${error}`}</div>
      </div>
    );
  }

  // No data available state
  if (!data || data.length === 0) {
    return (
      <div className="text-center">
        <h4>{title}</h4>
        <div>No content available</div>
      </div>
    );
  }

  // Data rendering
  return (
    <Container>
      <h4 className="feed-section-title mb-4">{title}</h4>
      <Row>
        {data.slice(0, 25).map((item, index) => (
          <Col md={4} key={index} className="mb-4">
            <Card className="feed-card h-100 shadow-lg border-light">
              <Card.Body>
                <Card.Title className="feed-card-title">{item.title || 'No Title'}</Card.Title>
                <Card.Subtitle className="mb-2 text-muted">
                  <strong>Bill Number:</strong> {item.bill_number || 'N/A'}
                </Card.Subtitle>
                <Card.Text>
                  <strong>Status:</strong> {item.status_title || 'N/A'}
                  <br />
                  <strong>Chamber:</strong> {item.origin_chamber || 'N/A'}
                  <br />
                  <strong>Committee:</strong> {item.committee || 'N/A'}
                  <br />
                  <strong>Created At:</strong> {item.created_at || 'N/A'}
                </Card.Text>
                <Card.Text>
                  <strong>Description:</strong> {item.description ? item.description.slice(0, 100) + '...' : 'No description available'}
                </Card.Text>
                <Button variant="primary" href={item.url} target="_blank" rel="noopener noreferrer">
                  More Details
                </Button>
              </Card.Body>
            </Card>
          </Col>
        ))}
      </Row>
    </Container>
  );
};

export default FeedSection;
```

### useFeedData Hook

The `useFeedData` hook is responsible for fetching data from the API.

```jsx
import { useState, useEffect } from 'react';

const useFeedData = (apiEndpoint, limit = 25) => {
  const [data, setData] = useState([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    const fetchData = async () => {
      try {
        const response = await fetch(apiEndpoint);
        if (!response.ok) throw new Error(`Error: ${response.statusText}`);

        const result = await response.json();
        setData(result);
      } catch (error) {
        setError(error.message);
      } finally {
        setLoading(false);
      }
    };

    fetchData();
  }, [apiEndpoint]);

  return { data, loading, error };
};

export default useFeedData;
```

## Conclusion

This project fetches and displays recent Congressional bills in a styled layout. It includes data fetching, error handling, and a responsive interface to accommodate various screen sizes. This `README.md` provides the necessary instructions for developers to set up the app, view the source code, and understand how the components are structured.
