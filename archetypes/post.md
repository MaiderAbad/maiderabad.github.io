---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
tags: ["flutter", "dart"]
summary: "This is my first post, I hope you like it."
draft: true
showTableOfContents: false
description: ""
showEdit: false
---

{{<badge>}}
New article!
{{</badge>}}

{{<alert>}}
**Warning!** This action is destructive!
{{</alert>}}

{{<alert "twitter">}}
Don't forget to [follow me](https://twitter.com/jpanther) on Twitter.
{{</alert>}}

### Blockquote without attribution

> Tiam, ad mint andaepu dandae nostion secatur sequo quae.
> **Note** that you can use _Markdown syntax_ within a blockquote.


Press <kbd>CTRL</kbd>+<kbd>ALT</kbd>+<kbd>Delete</kbd> to end the session.

Most <mark>salamanders</mark> are nocturnal, and hunt for insects, worms, and other small creatures.

<center>
{{<figure
    src="profile.jpeg"
    alt="Me with a dog"
    caption="Me with a dog [Disco Diffusion](https://github.com/alembics/disco-diffusion)."
	class="center_scaled"
   >}}
</center>



<center>
{{<figure
    src="disco_diffusion.png"
    alt="AI generated artwork"
    caption="AI generated art by [Disco Diffusion](https://github.com/alembics/disco-diffusion)."
    class="center_scaled"
   >}}
</center>

{{<badge>}}
New article!
{{</badge>}}

{{<button href="#button" target="_self">}}
Call to action
{{</button>}}
{{<badge>}}
New article!
{{</badge>}}

{{<alert>}}
**Warning!** This action is destructive!
{{</alert>}}

{{<alert "twitter">}}
Don't forget to [follow me](https://twitter.com/jpanther) on Twitter.
{{</alert>}}

{{<lead>}}
A powerful, lightweight theme for Hugo built with Tailwind CSS.
{{</lead>}}





{{<figure
    src="squid.jpeg"
    alt="Abstract purple artwork"
    caption="Photo by [Jr Korpa](https://unsplash.com/@jrkorpa) on [Unsplash](https://unsplash.com/)"
   >}}

<!-- OR -->

![Abstract purple artwork](squid.jpeg "Photo by [Jr Korpa](https://unsplash.com/@jrkorpa) on [Unsplash](https://unsplash.com/)")

{{<chart>}}
type: 'bar',
data: {
  labels: ['Tomato', 'Blueberry', 'Banana', 'Lime', 'Orange'],
  datasets: [{
    label: '# of votes',
    data: [12, 19, 3, 5, 2, 3],
  }]
}
{{</chart>}}


```dart
void main(){
    print("Hello World!");
}
```

Twitter
This example uses the twitter_simple shortcode to output a Tweet. It requires two named parameters user and id.

{{<twitter_simple user="DesignReviewed" id="1085870671291310081">}}

Alternatively, the tweet shortcode can be used to embed a fully marked up Twitter card.

![Image](/favicon.ico)

{{<highlight dark>}}
Highlighted text
{{</highlight>}}

{{<youtube w7Ft2ymGmfc>}}
{{<tweet user="itspsneha" id="1588207388418404352">}} <!--theme="dark"-->
{{<vimeo 146022717>}}


Emoji is supported throughout Congo by default. Emoji can be used in titles, menu items and article content.

{{<alert>}}
**Note:** The rendering of these glyphs depends on the browser and the platform. To style the emoji you can either use a third party emoji font or a font stack.
{{</alert>}}

Emoji replacements are automatic throughout Congo, so you can use shorthand codes in your content and front matter and they will be converted to their corresponding symbols at build time.

**Example:** `see_no_evil` :see_no_evil:, `hear_no_evil` :hear_no_evil:, `speak_no_evil` :speak_no_evil:.

The [Emoji cheat sheet](http://www.emoji-cheat-sheet.com/) is a useful reference for emoji shorthand codes.


This is a demo site built entirely using Congo. It also contains a complete set of [theme documentation]({{<ref "posts">}}). Congo is flexible and is great for both static page-based content (like this demo) or a traditional blog with a feed of recent posts.

Explore the [sample pages]("samples") to get a feel for what Congo can do. If you like what you see, check out the project on [Github](https://github.com/jpanther/congo) or read the [Installation guide](docs/installation) to get started.


![A stylised photograph of a purple squid on a pink backdrop.](squid.jpeg "Photo by [Jippe Joosten](https://unsplash.com/@jippe_joosten?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/s/photos/vibrant-purple?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText).")

| Icon name            | Preview                           |
| -------------------- | --------------------------------- |
| amazon               | {{<icon amazon>}}               |
| apple                | {{<icon apple>}}                |
| blogger              | {{<icon blogger>}}              |
| bug                  | {{<icon bug>}}                  |
| check                | {{<icon check>}}                |
| circle-info          | {{<icon circle-info>}}          |
| codepen              | {{<icon codepen>}}              |
| comment              | {{<icon comment>}}              |
| dev                  | {{<icon dev>}}                  |
| dribbble             | {{<icon dribbble>}}             |
| edit                 | {{<icon edit>}}                 |
| email                | {{<icon email>}}                |
| facebook             | {{<icon facebook>}}             |
| flickr               | {{<icon flickr>}}               |
| foursquare           | {{<icon foursquare>}}           |
| github               | {{<icon github>}}               |
| gitlab               | {{<icon gitlab>}}               |
| google               | {{<icon google>}}               |
| hashnode             | {{<icon hashnode>}}             |
| instagram            | {{<icon instagram>}}            |
| keybase              | {{<icon keybase>}}              |
| kickstarter          | {{<icon kickstarter>}}          |
| lastfm               | {{<icon lastfm>}}               |
| lightbulb            | {{<icon lightbulb>}}            |
| link                 | {{<icon link>}}                 |
| linkedin             | {{<icon linkedin>}}             |
| list                 | {{<icon list>}}                 |
| mastodon             | {{<icon mastodon>}}             |
| medium               | {{<icon medium>}}               |
| microsoft            | {{<icon microsoft>}}            |
| moon                 | {{<icon moon>}}                 |
| orcid                | {{<icon orcid>}}                |
| patreon              | {{<icon patreon>}}              |
| pencil               | {{<icon pencil>}}               |
| pinterest            | {{<icon pinterest>}}            |
| reddit               | {{<icon reddit>}}               |
| researchgate         | {{<icon researchgate>}}         |
| search               | {{<icon search>}}               |
| skull-crossbones     | {{<icon skull-crossbones>}}     |
| slack                | {{<icon slack>}}                |
| snapchat             | {{<icon snapchat>}}             |
| soundcloud           | {{<icon soundcloud>}}           |
| stack-overflow       | {{<icon stack-overflow>}}       |
| steam                | {{<icon steam>}}                |
| sun                  | {{<icon sun>}}                  |
| tag                  | {{<icon tag>}}                  |
| telegram             | {{<icon telegram>}}             |
| tiktok               | {{<icon tiktok>}}               |
| triangle-exclamation | {{<icon triangle-exclamation>}} |
| tumblr               | {{<icon tumblr>}}               |
| twitch               | {{<icon twitch>}}               |
| twitter              | {{<icon twitter>}}              |
| whatsapp             | {{<icon whatsapp>}}             |
| xmark                | {{<icon xmark>}}                |
| youtube              | {{<icon youtube>}}              |


This article offers a sample of basic Markdown formatting that can be used in Congo, also it shows how some basic HTML elements are decorated.

<!--more-->

## Headings

The following HTML `<h1>`—`<h6>` elements represent six levels of section headings. `<h1>` is the highest section level while `<h6>` is the lowest.

# H1

## H2

### H3

#### H4

##### H5

###### H6

## Paragraph

Xerum, quo qui aut unt expliquam qui dolut labo. Aque venitatiusda cum, voluptionse latur sitiae dolessi aut parist aut dollo enim qui voluptate ma dolestendit peritin re plis aut quas inctum laceat est volestemque commosa as cus endigna tectur, offic to cor sequas etum rerum idem sintibus eiur? Quianimin porecus evelectur, cum que nis nust voloribus ratem aut omnimi, sitatur? Quiatem. Nam, omnis sum am facea corem alique molestrunt et eos evelece arcillit ut aut eos eos nus, sin conecerem erum fuga. Ri oditatquam, ad quibus unda veliamenimin cusam et facea ipsamus es exerum sitate dolores editium rerore eost, temped molorro ratiae volorro te reribus dolorer sperchicium faceata tiustia prat.

Itatur? Quiatae cullecum rem ent aut odis in re eossequodi nonsequ idebis ne sapicia is sinveli squiatum, core et que aut hariosam ex eat.

## Blockquotes

The blockquote element represents content that is quoted from another source, optionally with a citation which must be within a `footer` or `cite` element, and optionally with in-line changes such as annotations and abbreviations.

### Blockquote without attribution

> Tiam, ad mint andaepu dandae nostion secatur sequo quae.
> **Note** that you can use _Markdown syntax_ within a blockquote.

### Blockquote with attribution

> Don't communicate by sharing memory, share memory by communicating.<br>
> — <cite>Rob Pike[^1]</cite>

[^1]: The above quote is excerpted from Rob Pike's [talk `about` nothing](https://www.youtube.com/watch?v=PAAkCSZUG1c) during Gopherfest, November 18, 2015.

## Tables

Tables aren't part of the core Markdown spec, but Hugo supports supports them out-of-the-box.

| Name  | Age |
| ----- | --- |
| Bob   | 27  |
| Alice | 23  |

### Inline Markdown within tables

| Italics   | Bold     | Code   |
| --------- | -------- | ------ |
| _italics_ | **bold** | `code` |

## Code Blocks

### Code block with backticks

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>Example HTML5 Document</title>
  </head>
  <body>
    <p>Test</p>
  </body>
</html>
```

### Code block indented with four spaces

    <!DOCTYPE html>
    <html lang="en">
    <head>
      <meta charset="utf-8">
      <title>Example HTML5 Document</title>
    </head>
    <body>
      <p>Test</p>
    </body>
    </html>

### Code block with Hugo's internal highlight shortcode

{{<highlight html "linenos=table,hl_lines=4 7-9">}}

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Example HTML5 Document</title>
</head>
<body>
  <p>Test</p>
</body>
</html>
{{</highlight>}}

## List Types

### Ordered List

1. First item
2. Second item
3. Third item

### Unordered List

- List item
- Another item
- And another item

### Nested list

- Fruit
  - Apple
  - Orange
  - Banana
- Dairy
  - Milk
  - Cheese

## Other Elements — abbr, sub, sup, kbd, mark

<abbr title="Graphics Interchange Format">GIF</abbr> is a bitmap image format.

H<sub>2</sub>O

X<sup>n</sup> + Y<sup>n</sup> = Z<sup>n</sup>

Press <kbd>CTRL</kbd>+<kbd>ALT</kbd>+<kbd>Delete</kbd> to end the session.

Most <mark>salamanders</mark> are nocturnal, and hunt for insects, worms, and other small creatures.


Mermaid diagrams are supported in Congo using the `mermaid` shortcode. Simply wrap the diagram markup within the shortcode. Congo automatically themes Mermaid diagrams to match the configured `colorScheme` parameter.

Refer to the [mermaid shortcode]( "docs/shortcodes#mermaid" ) docs for more details.

The examples below are a small selection taken from the [official Mermaid docs](https://mermaid-js.github.io/mermaid/). You can also [view the page source](https://raw.githubusercontent.com/jpanther/congo/dev/exampleSite/content/samples/diagrams-flowcharts.md) on GitHub to see the markup.

## Flowchart

{{<mermaid>}}
graph TD
A[Christmas] -->|Get money| B(Go shopping)
B --> C{Let me think}
B --> G[/Another/]
C ==>|One| D[Laptop]
C -->|Two| E[iPhone]
C -->|Three| F[Car]
subgraph Section
C
D
E
F
G
end
{{</mermaid>}}

## Sequence diagram

{{<mermaid>}}
sequenceDiagram
autonumber
par Action 1
Alice->>John: Hello John, how are you?
and Action 2
Alice->>Bob: Hello Bob, how are you?
end
Alice->>+John: Hello John, how are you?
Alice->>+John: John, can you hear me?
John-->>-Alice: Hi Alice, I can hear you!
Note right of John: John is perceptive
John-->>-Alice: I feel great!
loop Every minute
John-->Alice: Great!
end
{{</mermaid>}}

## Class diagram

{{<mermaid>}}
classDiagram
Animal "1" <|-- Duck
Animal <|-- Fish
Animal <--o Zebra
Animal : +int age
Animal : +String gender
Animal: +isMammal()
Animal: +mate()
class Duck{
+String beakColor
+swim()
+quack()
}
class Fish{
-int sizeInFeet
-canEat()
}
class Zebra{
+bool is_wild
+run()
}
{{</mermaid>}}

## Entity relationship diagram

{{<mermaid>}}
erDiagram
CUSTOMER }|..|{ DELIVERY-ADDRESS : has
CUSTOMER ||--o{ ORDER : places
CUSTOMER ||--o{ INVOICE : "liable for"
DELIVERY-ADDRESS ||--o{ ORDER : receives
INVOICE ||--|{ ORDER : covers
ORDER ||--|{ ORDER-ITEM : includes
PRODUCT-CATEGORY ||--|{ PRODUCT : contains
PRODUCT ||--o{ ORDER-ITEM : "ordered in"
{{</mermaid>}}


Congo includes support for Chart.js using the `chart` shortcode. Simply wrap the chart markup within the shortcode. Congo automatically themes charts to match the configured `colorScheme` parameter, however the colours can be customised using normal Chart.js syntax.

Refer to the [chart shortcode]("docs/shortcodes#chart") docs for more details.

The examples below are a small selection taken from the [official Chart.js docs](https://www.chartjs.org/docs/latest/samples). You can also [view the page source](https://raw.githubusercontent.com/jpanther/congo/dev/exampleSite/content/samples/charts.md) on GitHub to see the markup.

## Bar chart

<!-- prettier-ignore-start -->
{{<chart>}}
type: 'bar',
data: {
  labels: ['January', 'February', 'March', 'April', 'May', 'June', 'July'],
  datasets: [{
    label: 'My First Dataset',
    data: [65, 59, 80, 81, 56, 55, 40],
    backgroundColor: [
      'rgba(255, 99, 132, 0.2)',
      'rgba(255, 159, 64, 0.2)',
      'rgba(255, 205, 86, 0.2)',
      'rgba(75, 192, 192, 0.2)',
      'rgba(54, 162, 235, 0.2)',
      'rgba(153, 102, 255, 0.2)',
      'rgba(201, 203, 207, 0.2)'
    ],
    borderColor: [
      'rgb(255, 99, 132)',
      'rgb(255, 159, 64)',
      'rgb(255, 205, 86)',
      'rgb(75, 192, 192)',
      'rgb(54, 162, 235)',
      'rgb(153, 102, 255)',
      'rgb(201, 203, 207)'
    ],
    borderWidth: 1
  }]
}
{{</chart>}}
<!-- prettier-ignore-end -->

## Line chart

<!-- prettier-ignore-start -->
{{<chart>}}
type: 'line',
data: {
  labels: ['January', 'February', 'March', 'April', 'May', 'June', 'July'],
  datasets: [{
    label: 'My First Dataset',
    data: [65, 59, 80, 81, 56, 55, 40],
    tension: 0.2
  }]
}
{{</chart>}}
<!-- prettier-ignore-end -->

## Doughnut chart

<!-- prettier-ignore-start -->
{{<chart>}}
type: 'doughnut',
data: {
  labels: ['Red', 'Blue', 'Yellow'],
  datasets: [{
    label: 'My First Dataset',
    data: [300, 50, 100],
    backgroundColor: [
      'rgba(255, 99, 132, 0.7)',
      'rgba(54, 162, 235, 0.7)',
      'rgba(255, 205, 86, 0.7)'
    ],
    borderWidth: 0,
    hoverOffset: 4
  }]
}
{{</chart>}}
<!-- prettier-ignore-end -->