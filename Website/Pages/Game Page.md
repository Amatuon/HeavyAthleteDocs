# Game Page

**Overall Purpose:**

- Show details about a game including name, date(s), location, and description.
- Indicate if registration is open and provide a link to sign up (if logged in).
- If logged in and authorized, show options to view the game dashboard or manage athletes.
- Display a table of athletes competing in the game, including their scores (if available).
- Optionally show historic scores from our NASGA clone (if available).

**Content Breakdown:**

- **Content:**
    - **Game Name:** The name of the game.
    - **Game Dates:** Shows the start and end date of the game, formatted appropriately (single day vs. multi-day event).
    - **Location:** Displays the city, state, and country of the game.
    - **Registration:**
        - If registration is open:
            - Shows a message indicating registration is open and provides a link to sign up.
            - Conditionally adds a message requiring login if the user is not authenticated.
        - If registration is closed:
            - Shows different messages depending on if the game has already ended:
                - Before end date: Informs users registration is closed but they can still view information.
                - After end date: Informs users registration is closed.
    - **Description:** Displays a formatted version of the game description (if provided). ADs you can use [Markdown](https://www.markdownguide.org/basic-syntax/) here to make it look nice
    - **Actions:**
        - If registration is open, displays a message indicating registration is open and a link to sign up. Conditionally adds a message requiring login if the user is not authenticated.
        - If the user has permission to modify the game, shows a link to view the game dashboard.
    - **Athletes:**
        - Displays a table with athlete scores (if available):
            - Athlete scores are displayed in rows, grouped by flight type. Each flight type has its own header row. Scores are included from:
                - Current flights for the game (if available).
                - Historic flights from a NASGA clone (if available and not a first party game).
            - Pending scores section (conditionally displayed if the user has permission to modify the game):
                - A header row displays "Payment Pending".
                - Only the athlete in question and a site administrator have the ability to remove you from pending. Read [[I'm stuck at payment pending]] for more info.
