## Masonry Layout with TailwindCSS

CSS only Masonry layouts do not come without their faults, but I wanted to use something quick for a project I'm currently working on.

TailwindCSS doesn't currently support the properties I needed,  however, by adding 10 lines to my default css file, I had a couple of utility classes I could use...

```
@tailwind base;
@tailwind components;
@tailwind utilities;

/* Add the lines below */
@layer utilities {
  @variants responsive {
    .masonry {
      column-count: 2;
      column-gap: 1.5em;
    }
    .break-inside {
      break-inside: avoid;
    }
  }
}
``` 

Put simply, the .**masonry** class sets a number of columns and the gap between them. and the **.break-inside** class prevents content being able to split between columns.

You can use these classes alongside all other TailwindCSS classes, like so...

```
<div class="masonry before:box-inherit after:box-inherit">
  <div class="break-inside p-8 my-6 bg-gray-100 rounded-lg">
    <p>Really long content</p>
  </div>
  <div class="break-inside p-8 my-6 bg-gray-100 rounded-lg">
    <p>Really long content</p>
  </div>
  <div class="break-inside p-8 my-6 bg-gray-100 rounded-lg">
    <p>Really long content</p>
  </div>
...
</div>
``` 
You can view my example in the [Tailwind Playground](https://play.tailwindcss.com/h1aCTComsS?layout=horizontal )

Has anyone else ever needed this in TailwindCSS? Have you got another example of how it can be done?