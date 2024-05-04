## Simple helper functions

### 1. Create slug

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

### 2. Hexadecimal unique id

A function to create hexadecimal unique id.

```php
function getHexUniqueId(int $id, string $module){

    /**
     * Min 8-digit HexaDecimal value: 10000000 , Decimal value: 268435456
     * Max 8-digit HexaDecimal value: ffffffff , Decimal value: 4294967295
     *
     * Min 10-digit HexaDecimal value: 1000000000 , Decimal value: 68719476736
     * Min 10-digit HexaDecimal value: ffffffffff , Decimal value: 1099511627775
     *
     * Min 10-digit HexaDecimal value: 100000000000 , Decimal value: 17592186044416
     * Min 12-digit HexaDecimal value: ffffffffffff , Decimal value: 281474976710655
     */

    $time = dechex(time());     // 8 digit value

    $value_ranges = [
        'district'       => 70000000000000,
        'course'         => 70000100000000,
        'school'         => 70000300000000,
        'school_admin'   => 70000400000000,
        'district_admin' => 70000600000000,
        'event'          => 70000800000000,
        'section'        => 70001000000000,
        'contact'        => 70010000000000,
        'student'        => 70020000000000,
        'teacher'        => 70030000000000,
        'term'           => 70040000000000,
    ];

    if(!array_key_exists($module, $value_ranges)){
        return false;
    }

    $auto_id = (int) $value_ranges[$module] + (int) $id;

    $hex_dec_id = dechex((int) $auto_id);

    return $hex_dec_id . $time;
}
```

### 3.Week range selector

Get the starting day and last day of the week for a given date.

```php
function x_week_range($date) {
    $ts = strtotime($date);
    $start = (date('w', $ts) == 0) ? $ts : strtotime('last monday', $ts);
    return array(date('Y-m-d', $start),
                 date('Y-m-d', strtotime('next sunday', $start)));
}
```

And call it like this:

```php
list($start_date, $end_date) = x_week_range('2023-05-10');
```

### 4.Read csv file

Get the data from a csv file as an array.

```php
function read_from_csv($filepath){
	$file = fopen($filepath, "r");
	$arr = [];
	
	while (($data = fgetcsv($file, 1000, ",")) !== FALSE)
	{
	  $arr[] = $data;
	}
	
	fclose($file);
	
	return $arr;
}
```

### 5.Finding the number of days between two dates

Finding the no of days between two given days.

```php
$start_date = $request->start_date ?? date('Y-m-d');
$end_date = $request->end_date ?? date('Y-m-d');

$start_date_unix = strtotime($start_date);
$end_date_unix = strtotime($end_date);

$date_diff = round(($end_date_unix - $start_date_unix) / 86400);
```