# House of Commons Written Questions – Processed data

## Summary

This repo stores the processed data created by [`lchski/hoc-questions-analysis`](https://github.com/lchski/hoc-questions-analysis). It’s currently updated manually.

**The most comprehensive file is `questions_and_responses.csv`. If you’re doing analysis, you probably want to use it.**

## Variable details

Every file includes these variables (right hand side of each line is the variable type):

```
question_uid = col_character(),
parliament = col_double(),
session = col_double(),
question_number = col_double()
```

`question_uid` is a concatenation of `parliament`, `session`, and `question_number`, with `-` in between.

Here are the details about the files, with details of the extra variables:

- `questions_by_parliament.csv`: High-level information about questions (doesn’t include full question text, see `detailed_questions_by_parliament.csv`).
    ```
    question_sitting_day = col_double(),
    question_date = col_date(format = ""),
    question_title = col_character(),
    asker_name = col_character(),
    asker_riding = col_character(),
    number_of_responses = col_double()
    ```
- `detailed_questions_by_parliament.csv`: Much the same as `questions_by_parliament.csv`, plus full question text.
    ```
    question_sitting_day = col_double(),
    question_date = col_date(format = ""),
    asker_name = col_character(),
    asker_riding = col_character(),
    question_content = col_character()
    ```
- `responses_by_parliament.csv`: Information about responses, detailing the type of response and where to go to learn more.
    ```
    response_date = col_date(format = ""),
    response_sitting_day = col_double(),
    response_type = col_character(),
    response_detail = col_character(),
    response_details_full = col_character()
    ```
- `verbal_responses.csv`: Taking just the verbal questions from `responses_by_parliament.csv`, adds the full `response_content` from the _Debates_ (_Hansard_).
    ```
    response_sitting_day = col_double(),
    asker_name = col_character(),
    responder_name = col_character(),
    response_content = col_character()
    ```
- `questions_and_responses.csv`: The most comprehensive file, combining all the variables listed above. **You probably want to use this file for any analysis.**
    ```
    question_sitting_day = col_double(),
    question_date = col_date(format = ""),
    question_title = col_character(),
    question_content = col_character(),
    asker_name = col_character(),
    asker_riding = col_character(),
    number_of_responses = col_double(),
    response_date = col_date(format = ""),
    response_sitting_day = col_double(),
    response_type = col_character(),
    response_detail = col_character(),
    response_details_full = col_character(),
    responder_name = col_character(),
    response_content = col_character()
    ```

## Learn more

To see how these different files are put together, [take a look at the loading code from the main repo](https://github.com/lchski/hoc-questions-analysis/blob/master/load.R) (don’t forget [the secondary loading scripts](https://github.com/lchski/hoc-questions-analysis/tree/master/scripts/load)). It may not be the most self-explanatory—feel free to [get in touch if you have any questions](https://twitter.com/lchski).
