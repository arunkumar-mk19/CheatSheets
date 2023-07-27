# Simple helper functions

## 1. Create slug

```php

function createSlug($title, $separator = '-', $dictionary = ['@' => 'at'])
{

    // Convert all dashes/underscores into separator

    $flip = $separator === '-' ? '_' : '-';

    $title = preg_replace('!['.preg_quote($flip).']+!u', $separator, $title);

    // Replace dictionary words

    foreach ($dictionary as $key => $value) {
        $dictionary[$key] = $separator.$value.$separator;
    }

    $title = str_replace(array_keys($dictionary), array_values($dictionary), $title);

	// Remove all characters that are not the separator, letters, numbers, or whitespace

    $title = preg_replace('![^'.preg_quote($separator).'\pL\pN\s]+!u', '', mb_strtolower($title));

    // Replace all separator characters and whitespace by a single separator

    $title = preg_replace('!['.preg_quote($separator).'\s]+!u', $separator, $title);

    return trim($title, $separator);
}
```