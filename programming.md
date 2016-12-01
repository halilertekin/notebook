# programming

I find myself Googling same stuff every time I'm making something. This is for remembering programming tips/snippets that I learn and forget easily.

* [Bash](#bash)
* [Makefiles](#makefiles)

## CSS

#### Masonry Layout

```html
<article>
  <section>foo</section>
  <section>bar</section>
</article>
```

```css
article {
 -moz-column-width: 13em;
 -webkit-column-width: 13em;
 -moz-column-gap: 1em;
 -webkit-column-gap: 1em; 
}

section {
 display: inline-block;
 margin:  0.25rem;
 padding:  1rem;
 width:  100%; 
 background:  #efefef;
}
```

## Bash

### Conditions

#### Check if a variable is empty:

```bash
if [[ -z "${foobar// }" ]]; then
fi
```

#### Check if a variable is not empty:

```bash
[[ -n "${foobar// }" ]]
```

#### Check if a file exists:

```bash
if [ -f $FILE ];
then
   echo "File $FILE exists."
else
   echo "File $FILE does not exist."
fi
```

### loops

#### Iterate Files

```bash
for i in *; do echo $i; done
```

### dialogs

#### opening a menu with bunch of lines

```bash
regionsArray=()

while read i name; do
  regionsArray+=($i "$name")
done <<< "$regions"

selected=$(dialog --stdout \
                  --title "Timezones" \
                  --backtitle "Happy Hacking Linux" \
                  --ok-label "Next" \
                  --no-cancel \
                  --menu "Select a continent or ocean from the menu:" \
                  20 50 30 \
                  "${regionsArray[@]}")
```

## Makefiles

#### multiline strings

It's possible as long as the variable is exported

```make
export COMPONENT_HTML
create-component:
  define COMPONENT_HTML
import html from "choo/html"

const view = (state, prev, send) => html`
$(name)
`

export default view
```
  endef

  @echo "$$COMPONENT_HTML" > ui/components/${name}.js