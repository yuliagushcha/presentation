### CSS Grid Layout

> #### Slide 2
> CSS Grid Layout (aka "Grid"), is a two-dimensional grid-based layout system (meaning it can handle both columns and rows) that aims to do nothing less than completely change the way we design grid-based user interfaces.  
> CSS has always been used to lay out our web pages, but it's never done a very good job of it. First, we used tables, then floats, positioning and inline-block, but all of these methods were essentially hacks and left out a lot of important. Flexbox helped out, but it's intended for simpler one-dimensional layouts, not complex two-dimensional. Grid is the very first CSS module created specifically to solve the layout problems we've all been hacking our way around for as long as we've been making websites.  
> My intention with this presentation is to show the Grid concepts as they exist in the very latest version of the specification.

> #### Slide 3.1
> First of all, lets talk about basics and browser support

> #### Slide 3.2
> To get started you have to define a container element as a grid with ***display: grid***, set the column and row sizes with ***grid-template-columns*** and ***grid-template-rows***, and then place its child elements into the grid with ***grid-column*** and ***grid-row***.  
> Similarly to flexbox, the source order of the grid items doesn't matter. Your CSS can place them in any order, which makes it super easy to rearrange your grid with media queries. Imagine defining the layout of your entire page, and then completely rearranging it to accommodate a different screen width all with only a couple lines of CSS.

> #### Slide 3.3
> As of March 2017, most browsers shipped native, unprefixed support for CSS Grid: Chrome (including on Android), Firefox, Safari (including on iOS), and Opera. Internet Explorer 10 and 11 on the other hand support it, but it's an old implementation with an outdated syntax.  
> So, the time to build with grid is now!

> #### Slide 4.1
> Before diving into the concepts of Grid it's important to understand the terminology. Since the terms involved here are all kind of conceptually similar, it's easy to confuse them with one another if you don't first memorize their meanings defined by the Grid specification.

> #### Slide 4.2
> ***Grid Container*** is the element on which display: grid is applied. It's the direct parent of all the grid items. In this example container is the grid container.

> #### Slide 4.3
> ***Grid Item*** is the children of the grid container. Here the item elements are grid items, but sub-item isn't.

> #### Slide 4.4
> ***Grid Line*** is the dividing lines that make up the structure of the grid. They can be either vertical ("column grid lines") or horizontal ("row grid lines") and reside on either side of a row or column. Here the yellow line is an example of a column grid line.

> #### Slide 4.5
> ***Grid Track*** is the space between two adjacent grid lines. You can think of them like the columns or rows of the grid. Here's the grid track between the second and third row grid lines.

> #### Slide 4.6
> ***Grid Cell*** is the space between two adjacent row and two adjacent column grid lines. It's a single "unit" of the grid. Here's the grid cell between row grid lines 1 and 2, and column grid lines 2 and 3.

> #### Slide 4.7
> ***Grid Area*** is the total space surrounded by four grid lines. A grid area may be comprised of any number of grid cells. Here's the grid area between row grid lines 1 and 3, and column grid lines 1 and 3.

> #### Slide 5.1
> Now lets talk about properties for the grid container

> #### Slide 5.2
> ***Display*** defines the element as a grid container and establishes a new grid formatting context for its contents.  
> There are two main values: grid (generates a block-level grid) and inline-grid (generates an inline-level grid)

> #### Slide 5.3
> The next are ***grid-template-columns*** and ***grid-template-rows***. They define the columns and rows of the grid with a space-separated list of values. The values represent the track size, and the space between them represents the grid line.

> #### Slide 5.4
> If your definition contains repeating parts, you can use the ***repeat()*** notation to streamline things.

> #### Slide 5.5
> The ***fr*** unit allows you to set the size of a track as a fraction of the free space of the grid container. For example, this will set each item to one third the width of the grid container.

> #### Slide 5.6
> The next is ***grid-template-areas***, that defines a grid template by referencing the names of the grid areas which are specified with the grid-area property. Repeating the name of a grid area causes the content to span those cells.  
> That'll create a grid that's four columns wide by three rows tall. The entire top row will be comprised of the header area. The middle row will be comprised of two main areas, one empty cell, and one sidebar area. The last row is all footer.

> #### Slide 5.7
> ***grid-template*** is a shorthand for setting grid-template-rows, grid-template-columns, and grid-template-areas in a single declaration.  
> *none* sets all three properties to their initial values

> #### Slide 5.8
> ***grid-column-gap*** and ***grid-row-gap*** specify the size of the grid lines. You can think of it like setting the width of the gutters between the columns/rows.

> #### Slide 5.9
> ***grid-gap***, as grid-template, is a shorthand for grid-row-gap and grid-column-gap

> #### Slide 5.10
> ***justify-items*** aligns grid items along the inline (row) axis. This value applies to all grid items inside the container.  
> So:  
>> *start* aligns items to be flush with the start edge of their cell  
>> *end* aligns items to be flush with the end edge of their cell  
>> *center* aligns items in the center of their cell  
>> *stretch* fills the whole width of the cell

> #### Slide 5.11
> ***align-items*** aligns grid items along the block (column) axis (as opposed to justify-items which aligns along the inline (row) axis). The principle of operation of this property is the same as of justify-content.

> #### Slide 5.12
> ***Justify-content***  
> Sometimes the total size of your grid might be less than the size of its grid container. This could happen if all of your grid items are sized with non-flexible units like px. In this case you can set the alignment of the grid within the grid container. This property aligns the grid along the inline (row) axis.  
> To the standard values are added three new values:  
>> *space-around* places an even amount of space between each grid item, with half-sized spaces on the far ends  
>> *space-between* places an even amount of space between each grid item, with no space at the far ends  
>> *space-evenly* places an even amount of space between each grid item, including the far ends.

> #### Slide 5.13
> Property ***Align-content*** has the same values as justify-content, but it aligns the grid along the block (column) axis.

> #### Slide 5.14
> The next two properties are ***grid-auto-columns*** and ***grid-auto-rows***.  
> Both of it specify the size of any auto-generated grid tracks. Implicit tracks get created when there are more grid items than cells in the grid or when a grid item is placed outside of the explicit grid. 

> #### Slide 5.15
> If you have grid items that you don't explicitly place on the grid, the auto-placement algorithm kicks in to automatically place the items. The property ***grid-auto-flow*** controls how the auto-placement algorithm works. So, the value row - tells the auto-placement algorithm to fill in each row in turn, adding new rows as necessary; then the value column tells the auto-placement algorithm to fill in each column in turn, adding new columns as necessary; and the value dense tells the auto-placement algorithm to attempt to fill in holes earlier in the grid if smaller items come up later.

> #### Slide 5.16
> And the last property of grid container is ***grid***, that is a shorthand for setting all of the following properties in a single declaration: *grid-template-rows*, *grid-template-columns*, *grid-template-areas*, *grid-auto-rows*, *grid-auto-columns*, and *grid-auto-flow*.  
> For example, you have three properties: grid-template-roes, grid-auto-flow and grid-auto-columns.  
> The usage of the property grid looks like this.

> #### Slide 6.1
> Now let’s turn to the properties of grid-items.

> #### Slide 6.2
> Firstly, I say about ***grid-column-start***, ***grid-column-end***, ***grid-row-start*** and ***grid-row-end***. They determine a grid item's location within the grid by referring to specific grid lines. grid-column-start/grid-row-start is the line where the item begins, and grid-column-end/grid-row-end is the line where the item ends.

> #### Slide 6.3
> For example, you see, that these properties established in different ways: grid-column-start and grid-row-end as number, grid-column-end as number in words and grid-row-start as name of row. You can see the result of this code on the slide.

> ##### Slide 6.4
> Of course, there are properties, that is a shorthand for grid-column-start + grid-column-end, and grid-row-start + grid-row-end, respectively. They are ***grid-column*** and ***grid-row***.

> #### Slide 6.5
> As mentioned earlier, grid-items have a property called ***grid-area***.  
> It gives an item a name so that it can be referenced by a template created with the grid-template-areas property, and it looks like this.

> #### Slide 6.6
> The next properties – ***justify-self***, that aligns a grid item inside a cell along the inline (row) axis, and ***align-self***, that aligns a grid item inside a cell along the block (column) axis. The value of this properties applies to a grid item inside a single cell.

> #### Slide 6.7
> And the last property is ***place-self***, that sets both the align-self and justify-self properties in a single declaration.

> #### Slide 6.8
> Let's consider a small example of grid. On the slide you see his main layout. 

> #### Slide 6.9
> Next, we set the grid-area property for each item, the properties of the grid container, such as display: flex, grid-template-areas and grid-gap, and some properties of its design. Now let's look at the result. 

> #### Slide 6.10
> We see that the header occupies the entire first row, the menu occupies the next two rows of the first column, main and right are distributed on the remaining second row, and footer - the remaining third row.

> #### Slide 7
> So, thank you for your attention.  
> if you have any questions, you can ask them in the comments to this video.
