# Tables are Hard: Basic Demo

In this step, we add streaming data to a table that already has virtual scrolling, filtering, and sorting.
Then we update these existing features to account for the data rapidly changing underneath them.

How this was created:

- Modify `useData.js` and `App.js` to use data that adds a batch new rows every second, which shows several issues:
  - Scroll position jump to the top every time a batch is added
  - Virtual scrolling doesn't notice this until you scroll again
  - Sorting and column resizing both reset every time a batch comes in
- Fix sorting and column resizing with one-line settings changes for `react-table`
  - Set the default sort column to timestamp (ascending), so that new rows are appended at the bottom.
  - Clicking on the timestamp column to make it descending makes leaving the scrollbar at the top show updates live!
- Fix scroll resetting / rendering issues with a bit of React.memo juggling
