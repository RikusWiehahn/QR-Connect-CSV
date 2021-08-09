# Creating pages in bulk via CSV

To create a large number of QR Connect pages, you can use a CSV file containing each page in a long list format.

> HINT: Check out the examples at the bottom to get an idea of how a csv upload file should look.

#### Example file that creates two pages:

**[View Example CSV File Here](https://github.com/RikusWiehahn/QR-Connect-CSV/blob/main/example.csv)**

**[Download Example CSV File](https://github.com/RikusWiehahn/QR-Connect-CSV/archive/refs/tags/v1.0.zip)**

<br/>

## Contents

- [Setting up a page](#setting-up-a-page)
- [Common mistakes](#common-mistakes)
- [Section types](#section-types)
- [Headings](#headings)
- [Sub headings](#sub-headings)
- [Paragraphs](#paragraphs)
- [Links](#links)
- [YouTube videos](#youtube-videos)
- [Text based questions](#text-based-questions)
- [Single select questions](#single-select-questions)
- [Multi select questions or checklists](#multi-select-questions-or-checklists)
- [Image upload questions](#image-upload-questions)
- [Notification triggering questions](#notification-triggering-questions)
- [Full example](#full-example)

<br/>

# Getting started

1. Click the cog symbol next to the folder's title on a folder page.
2. Click the "Create pages using CSV" option
3. Upload a CSV file that follows the format described below.

<br/>

# Setting up a page

Each line in the CSV gives the page builder an instruction to start or stop a process or to enter a piece of information. These include:

- Start a new page
- Edit page info
- Start adding content onto a page
- Start a new page content section
- Edit page content section info
- End a page content section
- End adding content onto a page

<br/>

## Common mistakes

- Having an empty column between values, the page builder only reads the first two columns of any row.
- Spelling mistakes in any of the commands (new_page, published etc)
- Spelling mistakes in any of the section type identifiers (TEXT, HEADING_H1 etc)

## Required Page commands

The following lines tell the page builder what kind of page to create and when to finish building it.

| First word on a new line | Rest of that line                                  |
| ------------------------ | -------------------------------------------------- |
| `new_page`               | (leave rest of line empty)                         |
| `page_title`             | The title of the page to be created                |
| `page_type`              | Either: <br/> `STATIC_PAGE`<br/>`SUBMITTABLE_FORM` |
| `authentication`         | Either:<br/>`NONE`<br/>`PROJECT`<br/>`COMPANY`     |
| `published`              | Either:<br/>`TRUE`<br/>`FALSE`                     |
| `page_content_start`     | (leave rest of line empty)                         |
| [SECTION DATA SEE BELOW] | Instructions for the actual content of the page    |
| `page_content_end`       | (leave rest of line empty)                         |
| `page_end`               | (leave rest of line empty)                         |

<br/>

### Page types

QR Connect Pages can either be a basic page or fill-out form that allows page viewers to submit information to you.

- For a basic page, have `page_type` followed by `STATIC_PAGE`.
- For a submittable form, have `page_type` followed by `SUBMITTABLE_FORM`

<br/>

### Authentication

QR Connect pages can be set to be viewable to only members of a folder, members of an organization, or public.

- To only allow members of a folder, have `authentication` followed by `PROJECT`.
- To only allow members of your organization, have `authentication` followed by `COMPANY`.
- To make a page public have `authentication` followed by `PUBLIC`

<br/>

### Published or unpublished

QR Connect pages can either be published or in a draft state.

- To make a page published, have `published` followed by `TRUE`
- To make a page in draft, have `published` followed by `FALSE`

<br/>

# Section types

QR Connect pages are a list of smart sections or "blocks" that can be arranged in any order and allow you to do useful things. Here are the kinds of sections you can put into a page.

| Section type             | Description                                                          | Restrictions                     |
| ------------------------ | -------------------------------------------------------------------- | -------------------------------- |
| `HEADING_H1`             | Large heading                                                        | None                             |
| `HEADING_H2`             | Smaller heading                                                      | None                             |
| `TEXT`                   | Paragraphs                                                           | None                             |
| `LINK`                   | URL link                                                             | None                             |
| `YOUTUBE_VIDEO`          | Embedded YouTube video                                               | None                             |
| `TEXT_QUESTION`          | Question with input field                                            | Must be `SUBMITTABLE_FORM`       |
| `SINGLE_SELECT_QUESTION` | Question with multiple options but only one can be selected          | must be a `SUBMITTABLE_FORM`     |
| `MULTI_SELECT_QUESTION`  | Checklist with multiple options and many can be selected             | Must be a `SUBMITTABLE_FORM`     |
| `IMAGE_QUESTION`         | Question that asks a user to upload an image                         | Must be a `SUBMITTABLE_FORM`     |
| `NOTIFICATION_QUESTION`  | Yes / No question that sends an email alert depending on the answer. | Must be a `SUBMITTABLE_FORM`     |
| `PDF`                    | A PDF file                                                           | Can't be created using CSV files |
| `IMAGE`                  | An image                                                             | Can't be created using CSV files |
| `VIDEO`                  | A video                                                              | Can't be created using CSV files |

<br/>

# Full Section Formats

<br/>

## Headings

Identifier: `HEADING_H1`

Raw text in .csv file:

```
...
new_section
section_type, HEADING_H1
text, The heading you want...
section_end
...
```

In a spreadsheet

| First Column | Second Column           |
| ------------ | ----------------------- |
| ...          |                         |
| new_section  |                         |
| section_type | HEADING_H1              |
| text         | The heading you want... |
| section_end  |                         |
| ...          |                         |

<br/>

## Sub headings

Identifier: `HEADING_H2`

Raw text in .csv file:

```
...
new_section
section_type, HEADING_H2
text, The sub heading you want...
section_end
...
```

In a spreadsheet

| First Column | Second Column               |
| ------------ | --------------------------- |
| ...          |                             |
| new_section  |                             |
| section_type | HEADING_H2                  |
| text         | The sub heading you want... |
| section_end  |                             |
| ...          |                             |

<br/>

## Paragraphs

Identifier: `TEXT`

Raw text in .csv file:

```
...
new_section
section_type, TEXT
text, The paragraph you need...
section_end
...
```

In a spreadsheet

| First Column | Second Column             |
| ------------ | ------------------------- |
| ...          |                           |
| new_section  |                           |
| section_type | TEXT                      |
| text         | The paragraph you need... |
| section_end  |                           |
| ...          |                           |

<br/>

## Links

Identifier: `LINK`

Raw text in .csv file:

```
...
new_section
section_type, LINK
url, https://example.com
label, Example website link
section_end
...
```

In a spreadsheet

| First Column | Second Column        |
| ------------ | -------------------- |
| ...          |                      |
| new_section  |                      |
| section_type | LINK                 |
| url          | https://example.com  |
| label        | Example website link |
| section_end  |                      |
| ...          |                      |

<br/>

## Youtube videos

Identifier: `YOUTUBE_VIDEO`

Raw text in .csv file:

```
...
new_section
section_type, YOUTUBE_VIDEO
url, https://www.youtube.com/watch?v=y6120QOlsfU
section_end
...
```

In a spreadsheet

| First Column | Second Column                               |
| ------------ | ------------------------------------------- |
| ...          |                                             |
| new_section  |                                             |
| section_type | YOUTUBE_VIDEO                               |
| url          | https://www.youtube.com/watch?v=y6120QOlsfU |
| section_end  |                                             |
| ...          |                                             |

<br/>

## Text based questions

Identifier: `TEXT_QUESTION`

- `required` can be followed by `TRUE` of `FALSE`

Raw text in .csv file:

```
...
new_section
section_type, TEXT_QUESTION
text, "What is your name?"
required, FALSE
section_end
...
```

In a spreadsheet

| First Column | Second Column      |
| ------------ | ------------------ |
| ...          |                    |
| new_section  |                    |
| section_type | TEXT_QUESTION      |
| text         | What is your name? |
| required     | FALSE              |
| section_end  |                    |
| ...          |                    |

<br/>

## Single select questions

Identifier: `SINGLE_SELECT_QUESTION`

- `required` can be followed by `TRUE` of `FALSE`

Raw text in .csv file:

```
...
new_section
section_type, SINGLE_SELECT_QUESTION
text, What is your preferred pizza?
required, FALSE
answer, Pepperoni
answer, Hawaiian
answer, Vegetarian
answer, Meat lovers
section_end
...
```

In a spreadsheet

| First Column | Second Column                 |
| ------------ | ----------------------------- |
| ...          |                               |
| new_section  |                               |
| section_type | SINGLE_SELECT_QUESTION        |
| text         | What is your preferred pizza? |
| required     | FALSE                         |
| answer       | Pepperoni                     |
| answer       | Hawaiian                      |
| answer       | Vegetarian                    |
| answer       | Meat lovers                   |
| section_end  |                               |
| ...          |                               |

<br/>

## Multi select questions or checklists

Identifier: `MULTI_SELECT_QUESTION`

- `required` can be followed by `TRUE` of `FALSE`

Raw text in .csv file:

```
...
new_section
section_type, MULTI_SELECT_QUESTION
text, Do you believe any of the following?
required, FALSE
answer, The Illuminati control everything
answer, The pyramids were built by aliens
answer, The moon landing was faked
answer, Life is a simulation
answer, The earth is flat
section_end
...
```

In a spreadsheet

| First Column | Second Column                        |
| ------------ | ------------------------------------ |
| ...          |                                      |
| new_section  |                                      |
| section_type | MULTI_SELECT_QUESTION                |
| text         | Do you believe any of the following? |
| required     | FALSE                                |
| answer       | The Illuminati control everything    |
| answer       | The pyramids were built by aliens    |
| answer       | The moon landing was faked           |
| answer       | Life is a simulation                 |
| answer       | The earth is flat                    |
| section_end  |                                      |
| ...          |                                      |

<br/>

## Image upload questions

Identifier: `IMAGE_QUESTION`

- `required` can be followed by `TRUE` of `FALSE`

Raw text in .csv file:

```
...
new_section
section_type, IMAGE_QUESTION
text, Please upload an image of the damaged item
required, TRUE
section_end
...
```

In a spreadsheet

| First Column | Second Column                              |
| ------------ | ------------------------------------------ |
| ...          |                                            |
| new_section  |                                            |
| section_type | IMAGE_QUESTION                             |
| text         | Please upload an image of the damaged item |
| required     | TRUE                                       |
| section_end  |                                            |
| ...          |                                            |

<br/>

## Notification triggering questions

Identifier: `NOTIFICATION_QUESTION`

- `required` can be followed by `TRUE` of `FALSE`
- `notify_if` can be followed by `YES`, `NO`, or `NONE`
- `notification_text` is followed by the alert message you want to be sent
- `group_to_notify` can be followed by `PROJECT_MEMBERS`, `PROJECT_ADMINS`, `COMPANY_MEMBERS`, `COMPANY_ADMINS`, `NONE` depending on who you want to be notified.

Raw text in .csv file:

```
...
new_section
section_type, NOTIFICATION_QUESTION
text, Do you agree to these conditions?
notify_if, NO
required, TRUE
notification_text, Someone has declined the conditions...
group_to_notify, PROJECT_MEMBERS
section_end
...
```

In a spreadsheet

| First Column      | Second Column                          |
| ----------------- | -------------------------------------- |
| ...               |                                        |
| new_section       |                                        |
| section_type      | NOTIFICATION_QUESTION                  |
| text              | Do you agree to these conditions?      |
| notify_if         | NO                                     |
| required          | TRUE                                   |
| notification_text | Someone has declined the conditions... |
| group_to_notify   | PROJECT_MEMBERS                        |
| section_end       |                                        |
| ...               |                                        |

<br/>
<br/>

# Full Example

A submittable form for a QR code that gets scanned when a piece of equipment is broken:

Raw text in .csv file

```
new_page
page_title, Machine 408
page_type, SUBMITTABLE_FORM
authentication, NONE
published, TRUE
page_content_start
new_section
section_type, TEXT
text, Please report an issue by filling out the form
section_end
new_section
section_type, SINGLE_SELECT_QUESTION
text, How badly broken is it?
required, TRUE
answer, It's unusable
answer, On it's last legs
answer, Requires attention in the next 3 months
answer, It's just behaving abnormally
section_end
new_section
section_type, TEXT_QUESTION
text, Describe the problem in detail is needed
required, FALSE
section_end
new_section
section_type, IMAGE_QUESTION
text, Please upload an image of the damage if needed
required, FALSE
section_end
new_section
section_type, NOTIFICATION_QUESTION
text, Is this issue preventing anyone from doing their job?
notify_if, YES
required, TRUE
notification_text, Potential work stoppage caused by machine 408
group_to_notify, COMPANY_ADMINS
section_end
page_content_end
page_end

```

<br/>

In a spreadsheet:

| First Column       | Second Column                                         |
| ------------------ | ----------------------------------------------------- |
| new_page           |                                                       |
| page_title         | Machine 408                                           |
| page_type          | SUBMITTABLE_FORM                                      |
| authentication     | NONE                                                  |
| published          | TRUE                                                  |
| page_content_start |                                                       |
| new_section        |                                                       |
| section_type       | TEXT                                                  |
| text               | Please report an issue by filling out the form        |
| section_end        |                                                       |
| new_section        |                                                       |
| section_type       | SINGLE_SELECT_QUESTION                                |
| text               | How badly broken is it?                               |
| required           | TRUE                                                  |
| answer             | It's unusable                                         |
| answer             | On it's last legs                                     |
| answer             | Requires attention in the next 3 months               |
| answer             | It's just behaving abnormally                         |
| section_end        |                                                       |
| new_section        |                                                       |
| section_type       | TEXT_QUESTION                                         |
| text               | Describe the problem in detail is needed              |
| required           | FALSE                                                 |
| section_end        |                                                       |
| new_section        |                                                       |
| section_type       | IMAGE_QUESTION                                        |
| text               | Please upload an image of the damage if needed        |
| required           | FALSE                                                 |
| section_end        |                                                       |
| new_section        |                                                       |
| section_type       | NOTIFICATION_QUESTION                                 |
| text               | Is this issue preventing anyone from doing their job? |
| notify_if          | YES                                                   |
| required           | TRUE                                                  |
| notification_text  | Potential work stoppage caused by machine 408...      |
| group_to_notify    | COMPANY_ADMINS                                        |
| section_end        |                                                       |
| page_content_end   |                                                       |
| page_end           |                                                       |

<br/>

## Resulting QR Page

<img src="https://raw.githubusercontent.com/RikusWiehahn/QR-Connect-CSV/main/preview.png" alt="Preview" width="540"/>
