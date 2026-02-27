---
title: Custom overrides through frontmatter
ledger:
  preset: palmleaf
  palette:
    accent: red
---

# Custom overrides through frontmatter

---

In `config.yml`:

```
remote_theme: AninditaBasu/ledger
plugins:
  - jekyll-remote-theme
```

In the frontmatter of this page:

```
ledger:
  preset: palmleaf
  palette:
    accent: red
```

---

- [Headings](#headings)
- [Paragraphs](#paragraphs)
- [Lists](#lists)
- [Tables](#tables)
- [Codes](#codes)
- [Admonitions](#admonitions)
- [Images](#images)
- [Mermaid diagrams](#mermaid-diagrams)

---

## Headings

# This is heading 1

## This is heading 2

### This is heading 3

#### This is heading 4

---
 
## Paragraphs

Meghaduta is a lyric poem written by Kalidasa (c. 4th–5th century CE), considered to be one of the greatest Sanskrit poets. It describes how a _yaksha_, who had been banished by his master to a remote region for a year, asked a cloud to take a message of love to his wife. The poem become well-known in Sanskrit literature and inspired other poets to write similar poems (known as messenger-poems or Sandesha Kavya) on similar themes.

*[yaksha]: N. of a class of demigods who are described as attendants of Kubera, the god of riches, and employed in guarding his gardens and treasures; यक्षोत्तमा यक्षपतिं धनेशं रक्षन्ति वै प्रासगदादिहस्ताः Hariv.; Me.68; Bg.10.23;11.22.

---

## Lists

### Unordered list

- A glass bottle with a lid
- A piece of parchment that can be rolled up to fit inside the glass bottle
- A quill pen
- A bottle of ink
- An oilskin pouch that can fit inside the glass bottle

### Ordered list

1.  Clean the glass bottle thoroughly and put it out to dry.
1.  Dip the quill pen into the ink and write a message on the parchment.
1.  Wait for the ink to dry, and then fold the parchment and place it inside the oilskin pouch.
1.  Place the pouch inside the glass bottle and seal it.
1.  Determine the time of the next high tide by referring to the [tides table](#tables).
1.  At the next high tide, walk out to the sea and throw the glass bottle out as far as you can.

### Definition list

I can't open the chest
: Find the key. If the key is missing, take a crowbar and prise open the lid.

My letter was washed out by a cloudburst
: Write the letter again. Then, rub a piece of wax all over it.

---
 
## Tables

| Date      | First tide | Second tide |
| --------- | ---------- | ----------- |
| Fri Apr 1 | 10:44 AM   | 10:28 PM    |
| Sat Apr 2 | 11:28 AM   | 10:59 PM    |
| Sun Apr 3 | 12:12 PM   | 11:32 PM    |
| Mon Apr 4 | 12:58 PM   | 12:08 AM    |

---

## Codes

In code blocks, long lines are soft-wrapped.

```
tk.Label(root, text='Directory with the DITA files:', font=font_regular, bg=window_background_colour, justify='left', anchor='w', height=2).grid(row=0, column=0, sticky='w', padx=10, pady=5)
```

Inline code is rendered like this: `pip install google-generativeai pillow`.

To highlight keyboard keys, use HTML tags in your Markdown file. For example, 

```
Press <kbd>Ctrl</kbd> + <kbd>S</kbd> to save.
```

Rendered like this: Press <kbd>Ctrl</kbd> + <kbd>S</kbd> to save.

---

## Admonitions

{% include admonition.html
   type="note"
   title="Note"
   content="This is a basic note."
%}

{% include admonition.html
   type="warning"
   title="Warning"
   content="This one's a warning."
%}

{% include admonition.html
   type="tip"
   title="Tip"
   content="And now, a tip."
%}

{% include admonition.html
   type="caution"
   title="Caution"
   content="And a cautionary note."
%}

---

## Images

Images are centered.

![Site logo]({{ '/images/logo.png' | relative_url }})

---

## Mermaid diagrams

```mermaid
graph TD
A[Start] --> B{Decision}
B -->|Yes| C[Do thing]
B -->|No| D[Stop]
```

