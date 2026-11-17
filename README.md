# Bookboost guest and reservation exercise

> [!NOTE]
> You'll do this exercise live in the interview, together with the panel. Our expectation is that it should take about 45 minutes.
>
> No preparation is expected. If you'd like, feel free to spend up to 30 minutes looking at the data beforehand, but please don't build anything.
>
> Most importantly, we'd like to understand your process and the assumptions you make, rather than see a finished answer. You aren't expected to answer every question or find every data issue.

### Terms

For the sake of clarity, here are a few terms you'll come across in the data.

- **Gross and net.** Each reservation has a `total_gross_amount` and a `total_net_amount`, and both amounts are in EUR.
- **Booker and primary guest.** `reservation_guests` links a guest to a reservation. `role` is how that guest is involved, such as `booker`, `primary_guest`, or `companion`, and `is_primary` is `true` or `false`.
- **Reservation status.** `status` on `reservations` shows where the reservation is in its lifecycle, for example tentative or optional, confirmed, waitlist, checked in, checked out, cancelled, or no-show.

## Summary

At Bookboost, data models serve product, analytics, and machine learning. This exercise is a short version of that work. It uses a synthetic hotel guest and reservation dataset.

None of this work will be used by Bookboost. We want to see how you approach the problem.

Load the data, shape two models, and answer four questions. The AI tools and the environment are your choice. The way you work matters more than the final numbers. Explain your decisions. Ask questions as you go.

## Data

The data is synthetic. Email addresses use the domains example.com, example.org, and example.net. Phone numbers are fictional.

The CSV files are in the `data` folder. The same files are in `data/bookboost_guest_data.zip`. Load the files into a local database in raw form. Do not change the files before you load them.

Amounts are in EUR.

### properties

This table lists the hotels in the file.

- `property_uuid`
- `property_name`
- `property_group_uuid`
- `property_group_name`
- `city`
- `country_code`
- `currency`
- `timezone`
- `opened_on`

### guests

- `guest_uuid`
- `first_name`
- `last_name`
- `date_of_birth`
- `language_code`
- `country_code`
- `created_at`
- `updated_at`

### guest_emails

A guest can have more than one email row.

- `guest_email_uuid`
- `guest_uuid`
- `email`
- `is_primary`
- `created_at`

### guest_phones

A guest can have more than one phone row.

- `guest_phone_uuid`
- `guest_uuid`
- `phone_number`
- `raw_phone`
- `is_primary`
- `created_at`

### reservations

- `reservation_uuid`
- `property_uuid`
- `status`
- `booked_on`
- `arrival_date`
- `departure_date`
- `adults`
- `children`
- `currency`
- `total_gross_amount`
- `total_net_amount`
- `room_type`
- `source_reservation_id`
- `created_at`
- `updated_at`

### reservation_guests

This table links reservations and guests.

- `reservation_guest_uuid`
- `reservation_uuid`
- `guest_uuid`
- `is_primary`
- `role`
- `created_at`

## Expected output

Load the raw files into a local database. Inspect the raw data. State your assumptions. Ask questions when you need to.

Build two models in Python or SQL.

1. `guests`: one table for guests, with their contact details on that table.
2. `reservations`: one prepared table. The primary key is `reservation_uuid`. The table has a foreign key to `guests`.

Join the models in the way you choose. Use them to answer the questions below.

### Definitions

[Average length of stay (ALOS)](https://www.xotels.com/en/glossary/alos-average-length-of-stay) is the average length of a guest's stay over a period. The formula is the number of room nights divided by the number of bookings.

[Lead time](https://www.xotels.com/en/glossary/lead-time-restriction) is the time between when a reservation is made and the guest's arrival.

For the monthly metrics, discuss and document assumptions such as which date determines the month, how to handle stays spanning months, and which reservation statuses to include.

### Questions

1. Which guest has the highest total spend for the period 1st January 2026 to 31st July 2026?
2. What is the average number of reservations per guest across the dataset?
3. What is the average length of stay (ALOS) per month?
4. What is the average lead time per month?

## Guidance

There is no set tool, editor, or coding agent for this exercise. Choose the AI tools and the environment you want to use.

Show how you inspect the data, how you shape the models, and how you check the results. Document the assumptions behind each answer. A clear assumption is more useful than a silent number.

We will talk through your work in the interview. We will ask about your assumptions, your checks, and the way you used AI.
