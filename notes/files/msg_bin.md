# Message `.bin`

**File structure**
| Section              |
| :------------------- |
| File Header          |
| Message Section |
| Message ID Section   |


## Sections

### File Header

Header entry is 16-byte length with the following structure:

| Length | Type   | Description         |
| :----- | :----- | :------------------ |
| 4 byte | UInt32 | Message Offset |
| 4 byte | UInt32 | Message ID Offset   |
| 4 byte | UInt32 | Dummy 1             |
| 4 byte | Unit32 | Dummy 2             |

The purpose of `dummy 1` and `dummy 2` is unknown, currently it is just filled with `0x00`. 

We can calculate the size of each section using the first entry of header sections:

- `Header Section` Size = First Message Offset
- `Message Section` Size = First Message ID Offset - First Message Offset
- `Message ID Section` Size = File Size - First Message ID Offset

### Message Section

This section contains a `Null-terminated` `UTF-16` string, so the end of the text will be `0x0000`.

There are also special tags that will be described below.

### Message ID Section

This section contains a `Null-terminated` `UTF-16` string, so the end of the text will be `0x0000`.

The game will load text based on this entry.

## Special tags

All special tags are written in string, we can put a tag as another tag parameter so it is nestable.

**Tags without parameter**
| Description | Tag |
| :---------- | --- |
| Player Name | `<playername>` |
| Wait for button press | `<button>` |
| Clear text box | `<clear>` |

**Tags with parameters**
| Description | Tag | Example |
| :---------- | --- | :-- |
| Wait n milliseconds | `<wait:number_of_milisecond>` | `<wait:500>` will wait for 500 ms |
| Change face of selected character | `<face:char_id:expression_id>` | `<face:10:3>` char_id and expression_id will be describe later |
| Play sound effect | `<se:sound_effect_id>` | `<se:524295>` sound_effect_id will be describe later |
| Text base on player gender | `<GenderPlayer:male_text:female_text:non_biner_text>` | `<GenderPlayer:sir:madam:<playername>>` will display: sir (He/Him), madam (She/Her), player name (They/Them) |
| Text base on child gender | `<GenderChild:male_text:female_text>` | `<GenderChild:boy:girl>` will display: boy (male child), girl (female child) |
