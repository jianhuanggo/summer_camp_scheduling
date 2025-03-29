# Summer Camp Scheduling Application

A comprehensive web scheduling application for Aaron to efficiently organize summer camp events.

## Features

- **Event Selection**: Browse and select from a list of available summer camp events
- **Timeframe Input**: Set specific dates and times for scheduling events
- **Multiple Scheduling Methods**:
  - **Standard**: Schedule events based on priority
  - **With Breaks**: Add breaks between scheduled events
  - **By Category**: Group events by category for better organization
- **Responsive Design**: Works on desktop and mobile devices

## Technology Stack

- **Backend**: Python with FastAPI
- **Frontend**: React with TypeScript
- **UI Components**: Tailwind CSS and shadcn/ui
- **Data Storage**: In-memory database (for demonstration purposes)

## Project Structure

```
summer_camp_scheduling/
├── scheduling_backend/       # Python FastAPI backend
│   └── app/
│       ├── main.py           # Main FastAPI application
│       ├── models.py         # Data models
│       ├── data.py           # Sample event data
│       └── scheduler.py      # Scheduling algorithms
│
└── scheduling_frontend/      # React frontend
    ├── src/
    │   ├── App.tsx           # Main application component
    │   ├── types/            # TypeScript type definitions
    │   ├── services/         # API service functions
    │   └── components/       # React components
    └── .env                  # Environment configuration
```

## Setup and Installation

### Backend Setup

1. Navigate to the backend directory:
   ```
   cd scheduling_backend
   ```

2. Install dependencies using Poetry:
   ```
   poetry install
   ```

3. Run the FastAPI development server:
   ```
   poetry run fastapi dev app/main.py
   ```

4. The backend API will be available at http://localhost:8000

### Frontend Setup

1. Navigate to the frontend directory:
   ```
   cd scheduling_frontend
   ```

2. Install dependencies:
   ```
   npm install
   ```

3. Run the development server:
   ```
   npm run dev
   ```

4. The frontend will be available at http://localhost:5173

## API Endpoints

- `GET /api/events`: Get all available events
- `POST /api/schedule`: Schedule events using standard method
- `POST /api/schedule/with-breaks`: Schedule events with breaks
- `POST /api/schedule/by-category`: Schedule events grouped by category
- `GET /api/scheduled-events`: Get currently scheduled events

## Scheduling Algorithm

The scheduling algorithm takes selected events and a timeframe as input, then schedules the events within that timeframe based on the chosen method:

1. **Standard Method**: Events are scheduled based on priority (lower number = higher priority)
2. **With Breaks Method**: Adds specified break durations between events
3. **By Category Method**: Groups events by category before scheduling

The algorithm ensures that:
- Events do not overlap
- All events fit within the specified timeframe
- Event durations are respected
- Events are scheduled in a logical order

### Algorithm Implementation Details

The scheduling algorithm is implemented in `scheduler.py` and follows these steps:

1. **Input Validation**:
   - Verify that selected events exist
   - Ensure the timeframe is valid (start time before end time)
   - Check if all events can fit within the timeframe

2. **Event Sorting**:
   - Standard method: Sort by priority, then by duration
   - By Category method: Group by category, then sort by priority within each category

3. **Time Slot Allocation**:
   - Assign start and end times to each event
   - For the "With Breaks" method, add break durations between events
   - Ensure no events overlap and all fit within the timeframe

4. **Output Generation**:
   - Return a list of scheduled events with start and end times
   - Include all relevant event details in the output

## Usage

1. Browse the list of available events
2. Select events you want to schedule
3. Set the start and end dates/times for your schedule
4. Choose a scheduling method
5. Click "Schedule Events" to generate your schedule
6. View your scheduled events in the "View Schedule" tab

## Error Handling

The application includes comprehensive error handling:

- Validation of timeframe input
- Checking if selected events fit within the timeframe
- Handling API request failures
- Providing user-friendly error messages

## Future Enhancements

- Persistent data storage
- User authentication
- Drag-and-drop event reordering
- Calendar view for scheduled events
- Export schedule to PDF or calendar format
