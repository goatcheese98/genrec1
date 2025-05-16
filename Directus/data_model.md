# Directus Data Model

This document outlines the data model for the Directus instance at [https://recipe-gen.directus.app/](https://recipe-gen.directus.app/).

## Collection: `recipes`

| Field Name          | Data Type                  | Required | UI                   | Hidden | Readonly | Special                                     | Notes/Description                   |
| ------------------- | -------------------------- | -------- | -------------------- | ------ | -------- | ------------------------------------------- | ----------------------------------- |
| `id`                | UUID                       | Yes      | (System Managed)     | Yes    | Yes      | Primary Key, Auto-generated                 | Unique identifier for the recipe    |
| `title`             | String                     | Yes      | Text Input           | No     | No       |                                             | The main title of the recipe        |
| `slug`              | String                     | Yes      | Text Input           | No     | No       | Auto-generates from `title` field           | URL-friendly version of the title   |
| `short_description` | Text                       | No       | Textarea             | No     | No       |                                             | A brief summary of the recipe       |
| `main_image`        | File                       | No       | Image Upload         | No     | No       |                                             | Primary image for the recipe        |
| `ingredients`       | JSON or Text               | No       | Repeater             | No     | No       | (e.g., list of ingredient items/text)       | Ingredients list for the recipe     |
| `instructions`      | Text                       | No       | Repeater             | No     | No       | (e.g., step-by-step instructions)           | Cooking instructions for the recipe |
| `prep_time`         | String or Integer          | No       | Text Input           | No     | No       | (e.g., "30 minutes" or 30)                  | Preparation time                    |
| `cook_time`         | String or Integer          | No       | Text Input           | No     | No       | (e.g., "1 hour" or 60)                      | Cooking time                        |
| `difficulty`        | String                     | No       | Select Dropdown      | No     | No       | (e.g., Options: Easy, Medium, Hard)         | Cooking difficulty level            |
| `status`            | String                     | No       | Select Dropdown      | No     | No       | (e.g., Options: draft, published, archived) | Publication status of the recipe    |
| `categories`        | Many-to-Many (`categories`) | No       | Relational Interface | No     | No       | Links to the `categories` collection        | Recipe categories                   |
| `tags`              | Array of Strings           | No       | Tags Input           | No     | No       | Stores a list of tag strings directly       | Recipe tags                         |
| `date_published`    | DateTime                   | No       | Datetime Picker      | No     | No       |                                             | Date when the recipe was published  |

## Collection: `blog_posts`

| Field Name       | Data Type               | Required | UI                   | Hidden | Readonly | Special                                     | Notes/Description                     |
| ---------------- | ----------------------- | -------- | -------------------- | ------ | -------- | ------------------------------------------- | ------------------------------------- |
| `id`             | UUID                    | Yes      | (System Managed)     | Yes    | Yes      | Primary Key, Auto-generated                 | Unique identifier for the blog post   |
| `title`          | String                  | Yes      | Text Input           | No     | No       |                                             | Title of the blog post                |
| `slug`           | String                  | Yes      | Text Input           | No     | No       | Auto-generates from `title` field           | URL-friendly version of the title     |
| `featured_image` | File                    | No       | Image Upload         | No     | No       |                                             | Main image for the blog post          |
| `content`        | Text                    | No       | WYSIWYG Editor       | No     | No       |                                             | Main content of the blog post         |
| `published_date` | DateTime                | No       | Date Picker          | No     | No       |                                             | Date when the blog post was published |
| `tags`           | Array of Strings        | No       | Tags Input           | No     | No       | Stores a list of tag strings directly       | Tags associated with the blog post    |
| `author`         | Many-to-One (`authors`) | No       | Relational Interface | No     | No       | Links to the `authors` collection           | Author of the blog post               |
| `status`         | String                  | No       | Radio Buttons        | No     | No       | (e.g., Options: draft, published, archived) | Publication status of the blog post   |

## Collection: `tags`

| Field Name | Data Type | Required | UI               | Hidden | Readonly | Special                     | Notes/Description               |
| ---------- | --------- | -------- | ---------------- | ------ | -------- | --------------------------- | ------------------------------- |
| `id`       | UUID      | Yes      | (System Managed) | Yes    | Yes      | Primary Key, Auto-generated | Unique identifier for the tag   |
| `name`     | String    | Yes      | Text Input       | No     | No       |                             | Name of the tag (e.g., "Vegan") |

## Collection: `categories`

| Field Name | Data Type | Required | UI               | Hidden | Readonly | Special                     | Notes/Description                       |
| ---------- | --------- | -------- | ---------------- | ------ | -------- | --------------------------- | --------------------------------------- |
| `id`       | UUID      | Yes      | (System Managed) | Yes    | Yes      | Primary Key, Auto-generated | Unique identifier for the category      |
| `name`     | String    | Yes      | Text Input       | No     | No       |                             | Name of the category (e.g., "Desserts") |

## Collection: `authors`

| Field Name | Data Type | Required | UI               | Hidden | Readonly | Special                     | Notes/Description                |
| ---------- | --------- | -------- | ---------------- | ------ | -------- | --------------------------- | -------------------------------- |
| `id`       | UUID      | Yes      | (System Managed) | Yes    | Yes      | Primary Key, Auto-generated | Unique identifier for the author |
| `name`     | String    | Yes      | Text Input       | No     | No       |                             | Name of the author               |
| `avatar`   | File      | No       | Image Upload     | No     | No       |                             | Profile picture of the author    |

## Junction Collection: `recipes_categories`

(Many-to-many relationship between `recipes` and `categories`)

| Field Name      | Data Type                  | Required | UI  | Hidden | Readonly | Special | Notes/Description              |
| --------------- | -------------------------- | -------- | --- | ------ | -------- | ------- | ------------------------------ |
| `id`            | Standard (Primary Key)     | Yes      |     |        |          |         | Auto-incrementing primary key  |
| `recipes_id`    | Many-to-One (`recipes`)    | Yes      |     |        |          |         | Foreign key to `recipes.id`    |
| `categories_id` | Many-to-One (`categories`) | Yes      |     |        |          |         | Foreign key to `categories.id` |