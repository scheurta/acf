# ACF

> An [Advanced Custom Fields](https://www.advancedcustomfields.com) helper for [WordPlate](https://wordplate.github.io).

[![Build Status](https://img.shields.io/travis/wordplate/acf/master.svg?style=flat)](https://travis-ci.org/wordplate/acf)
[![StyleCI](https://styleci.io/repos/87427318/shield?style=flat)](https://styleci.io/repos/87427318)
[![Coverage Status](https://img.shields.io/codecov/c/github/wordplate/acf.svg?style=flat)](https://codecov.io/github/wordplate/acf)
[![Latest Version](https://img.shields.io/github/release/wordplate/acf.svg?style=flat)](https://github.com/wordplate/acf/releases)
[![License](https://img.shields.io/packagist/l/wordplate/acf.svg?style=flat)](https://packagist.org/packages/wordplate/acf)

## Installation

Require this package, with [Composer](https://getcomposer.org/), in the root directory of your project.

```bash
$ composer require wordplate/acf
```

## Usage

Use the `acf_field_group()` helper function to register a new field group in ACF. It uses the [`acf_add_local_field_group()`](https://www.advancedcustomfields.com/resources/register-fields-via-php#example) function behind the scenes. The difference is that it appends the `key` value to all fields. Below you'll find an example of a field group.

```php
$fields = [
    acf_image(['name' => 'image', 'label' => 'Image']),
    acf_text(['name' => 'title', 'label' => 'Title']),
];

$location = [
    acf_location('post_type', 'post'),
    acf_location('post_type', '!=', 'page'),
];

acf_field_group([
    'title' => 'About',
    'fields' => $fields,
    'location' => [
        $location
    ],
]);
```

[Visit the official documentation to read more about the field group settings.](https://www.advancedcustomfields.com/resources/register-fields-via-php#group-settings)

## Fields

All fields accepts an array of settings. All field settings arrays must have the keys `label` and `name`. Below the example you'll find a list of available field functions.

```php
acf_text([
    'label' => 'Field Label'
    'name' => 'unique-field-name'
]);
```

### Settings

Below you'll find a list of settings and their descriptions you can add to your fields. [Visit the official documentation](https://www.advancedcustomfields.com/resources/register-fields-via-php#field-settings) to read more about the field settings.

Name | Description
---- | -----------
`label` | This is the label which appears on the edit page when entering a value.
`name` | This is the name used to save and load data from the database. This name must be a single word, no spaces, underscores and dashes allowed.
`type` | The type of field will change the settings available, the interface when entering data, and the value returned from the database.
`instructions` | This text appears on the edit page when entering a value.
`required` | Required fields will cause validation to run when saving a post. When attempting to save an empty value to a required field, an error message will display.
`conditional_logic` | Once enabled, more settings will appear to customize the logic which determines if the current field should be visible or not. Groups of conditional logic can be created to allow for multiple and/or statements. The available [toggle](#choice-fields) fields are limited to those which are of the type select, checkbox, true/false, radio.

### Basic Fields

- `acf_email()` - The email field creates a simple email input.
- `acf_number()` - The number field creates a simple number input.
- `acf_password()` - The password field creates a simple password input.
- `acf_range()` - The [range](https://www.advancedcustomfields.com/resources/range) field provides an interactive experience for selecting a numerical value.
- `acf_text()` - The [text field](https://www.advancedcustomfields.com/resources/text) creates a simple text input.
- `acf_textarea()` - The [textarea field](https://www.advancedcustomfields.com/resources/textarea) creates a simple textarea.
- `acf_url()` - The url field creates a simple url input.

### Choice Fields

- `acf_button_group()` - The button group field creates a list of radio buttons.
- `acf_checkbox()` - The [checkbox field](https://www.advancedcustomfields.com/resources/checkbox) creates a list of tick-able inputs.
- `acf_radio()` - The [radio button field](https://www.advancedcustomfields.com/resources/radio-button) creates a list of select-able inputs.
- `acf_select()` - The [select field](https://www.advancedcustomfields.com/resources/select) creates a drop down select or multiple select input.
- `acf_true_false()` - The [true / false field](https://www.advancedcustomfields.com/resources/true-false) allows you to select a value that is either 1 or 0.

### Content Fields

- `acf_file()` - The [file field](https://www.advancedcustomfields.com/resources/file) allows a file to be uploaded and selected.
- `acf_gallery()` - The [gallery field](https://www.advancedcustomfields.com/resources/gallery) provides a simple and intuitive interface for managing
- `acf_image()` - The [image field](https://www.advancedcustomfields.com/resources/image) allows an image to be uploaded and selected.
- `acf_oembed()` - The [oEmbed field](https://www.advancedcustomfields.com/resources/oembed) allows an easy way to embed videos, images, tweets, audio, and other content.
- `acf_wysiwyg()` - The [WYSIWYG field](https://www.advancedcustomfields.com/resources/wysiwyg-editor) creates a full WordPress tinyMCE content editor.

### jQuery Fields

- `acf_color_picker()` - The [color picker field](https://www.advancedcustomfields.com/resources/color-picker) allows a color to be selected via a JavaScript popup.
- `acf_date_picker()` - The [date picker field](https://www.advancedcustomfields.com/resources/date-picker) creates a jQuery date selection popup.
- `acf_date_time_picker()` - The [date time picker field](https://www.advancedcustomfields.com/resources/date-time-picker) creates a jQuery date & time selection popup.
- `acf_google_map()` - The [Google Map field](https://www.advancedcustomfields.com/resources/google-map) creates an interactive map with the ability to place a marker.
- `acf_time_picker()` - The [time picker field](https://www.advancedcustomfields.com/resources/time-picker) creates a jQuery time selection popup.

### Layout Fields

- `acf_clone()` - The [clone field](https://www.advancedcustomfields.com/resources/clone) allows you to select and display existing fields.
- `acf_flexible_content()` - The [flexible content field](https://www.advancedcustomfields.com/resources/flexible-content) acts as a blank canvas to which you can add an unlimited number of layouts with full control over the order.
- `acf_group()` - The [group](https://www.advancedcustomfields.com/resources/group) allows you to create a group of sub fields.
- `acf_message()` - The message fields allows you to display a text message.
- `acf_repeater()` - The [repeater field](https://www.advancedcustomfields.com/resources/repeater) allows you to create a set of sub fields which can be repeated again and again whilst editing content!
- `acf_tab()` - The [tab field](https://www.advancedcustomfields.com/resources/tab) is used to group together fields into tabbed sections. 

### Relational Fields

- `acf_link()` - The [page link field](https://www.advancedcustomfields.com/resources/link) provides a simple way to select or define a link (url, title, target).
- `acf_page_link()` - The [page link field](https://www.advancedcustomfields.com/resources/page-link) allows the selection of 1 or more posts, pages or custom post types.
- `acf_post_object()` - The [post object field](https://www.advancedcustomfields.com/resources/post-object) creates a select field where the choices are your pages + posts + custom post types. 
- `acf_relationship()` - The [relationship field](https://www.advancedcustomfields.com/resources/relationship) creates a very attractive version of the post object field. 
- `acf_taxonomy()` - The [taxonomy field](https://www.advancedcustomfields.com/resources/taxonomy) allows the selection of 1 or more taxonomy terms. 
- `acf_user()` - The user field creates a select field for all your users. 

## Helpers

This package provides three helper packages [`acf_conditional_logic()`](#acf_conditional_logic) and [`acf_location()`](#acf_location) to help you write less arrays for your field groups.

##### `acf_conditional_logic()`

The `acf_conditional_logic()` function help you write [conditional logic](#settings) without knowing the fields `key` value.

```php
acf_conditional_logic('type', 'image');

acf_conditional_logic('type', '!==' 'image');
```

##### `acf_location()`

The `acf_location()` function help you write `location` arrays without the `name`, `operator` and `value` keys.

```php
acf_location('post_type', 'post');

acf_location('post_type', '!=', 'post');
```

## License

[MIT](LICENSE) © [Vincent Klaiber](https://vinkla.com)
