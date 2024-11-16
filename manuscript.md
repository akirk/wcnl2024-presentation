Goal of the talk:
- Introduce the Try WordPress extension
- Explain Playground and the benefits

# Gather attention
- Trying WordPress Plugins is risky!
- WordPress is server-side only software!
- I don't need data liberation!
- Data exports from platforms are useless!

# Overview
- What is Data Liberation? Why is it meaning full to me? What can be WordPress' role?
- Big Detour to WordPress Playground:
  - What is it? How can it be relevant to you?
  - What can I build with it, how can I use it?
- Coming back to Data Liberation and how it can be combined with WordPress Playground

# What is Data Liberation?
It means the ability to use your data that you have in one system in another system. Usually, this means that you would export your data from one system and then import it into another system.

Since we're on a WordCamp and talking about WordPress, I mostly refer to web apps.

## Getting Data Out
Depending on legislation, some companies are required to provide you with a copy of your data in a format that can be used by other systems. This is called data portability.

When there is no such requirement, companies rarely provide this feature.

There are differences in how accessible this feature is. Sometimes it is implemented as a self-service feature, sometimes you have to contact support to get your data. Often it takes a while to get your data and it is delivered as a file or zipped files and directories.

In practice, importing the can be tricky, as the data may be stored in a format that cannot easily be imported into another system. There is little incentive for the industry to define common standards for data export and import. This is because companies only want to encourage the inflow to their company, not the outflow.

Defining a common format would restrict the ability to innovate and differentiate from competitors. Such a format would represent a lowest common denominator, resulting in a subpar experience and a lossy migration.

## WordPress has played a role as a transition platform

As open source software, WordPress has a number of importers and exporters available. This makes it a good transition platform. You can import data from a variety of sources and export it to a variety of destinations. This is especially useful when you are migrating from one system to another.

Importing tools don't get a lot of community attention as they are one-time tools. Once you've imported your data, you don't need the importer anymore. If an import is flawed, typically the data is touched up manually instead of fixing the importer problem and re-importing.

This results in a stagnating importing experience.

## WordPress Playground

In 2023, Adam Zieliński started to work on a new project called WordPress Playground. It makes use of a technology called WASM to run WordPress in the browser.

Why would you want to run WordPress in a browser? It is server-side software, right?

Turns out there are a number of use cases:
- Try out plugins without risking your live site
- Showcase a website before you have a host for it
- Run beta versions of WordPress or plugins to test them
- Translate a plugin that's actually running instead of guessing its UI

## Where will I come across Playground

You might have already seen the Preview button in the WordPress plugin directory. This is powered by Playground.

There was actually a little of a controversy when the button was first introduced because it was first implemented in a way that Playground was just instructed to boot WordPress and install the specific plugin.

It turns out that many plugins need some prerequisites to work well. Also, when you want to preview a plugin, you don't want to spend a lot of time configuring it.

## Experiment

So now, I'd like to give you the tools to make Playground useful for yourself.

Why would you want that? We just saw that you can just try a plugin with a preview button.

But why stop there?

## Only a Configured WordPress is a Useful WordPress

Let's face it, in it's standard configuration, WordPress is only mildly interesting.

Even if you just want to blog, you want to give it a personal touch.

If you want to use its power, you'll want to use plugins.

So, when you arrive on playground.wordpress.net this is exactly what you can do. You can use the Site Editor to customize your WordPress. This is already quite nice to try Core WordPress.

You can also go to wp-admin and install new plugins. And try them.

## Pre-configuring WordPress

What if you could configure your WordPress even faster?

Playground supports query parameters. You can set the theme by adding a `?theme=twentytwentytwo` to the URL. You can install a plugin by adding `&plugin=friends`.

With something called Blueprint, you can define a list of plugins to install, set the theme to use.

Try the Step Library

## Booting WordPress

An important aspect of WordPress Playground is that you can control what kind of WordPress it runs.

A blueprint is something you could call a "startup definition" file. It tells Playground what to do before it navigates the user to the first page inside playground.

## Built on Steps

One thing that we have learned as we built Blueprints is that there are many things that you can technically do with the existing steps but you really need to know them, and sometimes be clever about them.

This is why I have created the Step Library. It is a collection of steps that you can use to build your blueprints.

For example there is a step to add a page, or an admin notice.

## What can you build with Playground?

I don't know who you are and how you use WordPress. But if you take a look at the list of steps available, you might get some ideas.

## Where are we taking Playground?

One thing that's special about running WordPress in the browser is that you have to obey the same rules that any JavaScript web app is: you can only make requests to external servers that have CORS set up.

Using SQLite can be a blocker for some more complex plugins that take advantage of specific features of MySQL. We're working on a robust engine that can translate MySQL to SQLite.


## Technical detour for the really interested

## How does Playground work?

WordPress Playground uses PHP compiled so that it can run inside WebAssembly which is a sandbox environment. It also uses SQLite instead of MySQL as a database. Everything is stored locally in the browser. By default it is temporary but you can also ask the browser not to delete it and it will persist across sessions.

WordPress Playground provides a Web Worker that can intercept network requests. When the browser asks to navigate to a page that can be served by WordPress inside WASM, the worker intercepts the request and serves the page from WordPress.

To me it is fascinating that this works as well and as fast as it does.

## WordPress Playground and Importing

WordPress Playground changes the game because it is so fast and easy to try again from scratch. This makes it feasible to iterate on the import process until it is perfect. This is especially useful for developers who are working on importing tools.

By placing playground in the browser sidebar through an extension and importing into the "live" playground, we also avoid working with file formats.

We also have the advantage of working with the data as it is visible to the user which can be useful for JavaScript web apps where the data cannot be extracted from the HTML.

# What are data origins?
- Blogs (Posts, Pages)
- Business Representation Websites, e.g. restaurants (Pages, Menus)
- E-Commerce (Products)
- Social Networks (Posts, Connections)

## Data Formats

When importing to WordPress we want to give users choice. WordPress itself has support for a number of post types like pages or posts but beyond that we rely on plugins. Because of the ecosystem there is a variety of plugins available in the different areas, for example plugins providing a shopping system. A Data liberation project should not make these decisions for the user.

### How to achieve this?
We define some generic post types and attributes that we think are useful. The user can then assist the system by selecting where on the page the respective fields can be found.

For example: This is the product title, this is the price.

We have a few ideas for post types but we're hoping for community involvement to help us discover and define more.

When this generic type has been imported, the user can choose a plugin that can handle this type of content. We need user contributions for both the selection of plugins, as well as developer contributions to make their plugins capable of accepting these generic types.

## Advantages of a Live WordPress

- Live Previews of the imported data
- Plugins can use the typical mechanisms (WordPress hooks) to receive data and import it to their own data structures
- No need to find suitable file formats for storing and restoring the data

# Try WordPress Extension

## Development Goals
Build a test driven infrastructure that allows easy repeatable testing of the import flows

## Community Opportunities

- Contribute to exporting recipes
- Contribute to the extension itself
- Add support to plugins as desired targets


# Where can you help?

