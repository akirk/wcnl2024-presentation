Goal of the talk:
- Introduce the Try WordPress extension
- Explain Playground and the benefits

# Gather attention
- Trying WordPress Plugins is risky!
- WordPress is server-side only software!
- Data exports from platforms are useless!

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
