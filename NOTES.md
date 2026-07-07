## NOTES

## One Fix : 
I chose the double-booking bug. So what I did is check first the double booking bug in code and found out this line of code:

def dates_overlap(start_a, end_a, start_b, end_b):
    """True if date range A overlaps date range B."""
    return start_b <= start_a <= end_b

## This only checks whether the new booking's start date falls inside an existing booking.

It completely ignores these situations:

Existing:
Jan 10 ------------ Jan 15

New:
Jan 8 -------------------- Jan 20

The new booking starts before Jan 10, so

Jan10 <= Jan8 <= Jan15

is False.

Therefore the system incorrectly allows it.

## Correct implementation
def dates_overlap(start_a, end_a, start_b, end_b):
    """True if two date ranges overlap."""
    return start_a <= end_b and end_a >= start_b

## This detects every overlap case.

## Ai used for verifying

- I used chatgpt,  I sent the code and sample output to verify if it's correct..