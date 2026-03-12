# ConversationSearch

`ConversationSearch` uses the Search component, supporting search functionality for users, groups, and messages. It integrates features such as the search bar, advanced search, and search result display.

## Basic Usage

```
SearchResultItem
```

## Props

| **Parameter Name** | **Type** | **Default Value** | **Description** |
| --- | --- | --- | --- |
| visible | boolean | true | Whether it is visible. |
| [Search](/document/product/182866808150605824) | ComponentType<SearchProps> | - | custom search component |
| variant | VariantType | VariantType.MINI | Search mode: mini, standard, embedded |
| [SearchBar](/document/product/182866808150605824#.E8.87.AA.E5.AE.9A.E4.B9.89.E8.83.BD.E5.8A.9B) | React.ComponentType<SearchBarProps> | DefaultSearchBar | custom search bar component |
| [SearchResults](/document/product/182866808150605824#.E8.87.AA.E5.AE.9A.E4.B9.89.E8.83.BD.E5.8A.9B) | React.ComponentType<SearchResultsProps> | DefaultSearchResults | custom search result component |
| [SearchAdvanced](/document/product/182866808150605824#.E8.87.AA.E5.AE.9A.E4.B9.89.E8.83.BD.E5.8A.9B) | React.ComponentType<SearchAdvancedProps> | DefaultSearchAdvanced | custom advanced search component |
| SearchResultsPresearch | React.ComponentType | - | search placeholder component |
| SearchResultsLoading | React.ComponentType | - | loading placeholder component |
| SearchResultsEmpty | React.ComponentType | - | empty result placeholder component |
| SearchResultItem | React.ComponentType<ResultItemProps> | - | custom search result item component |
| debounceTime | number | 300 | search debounce time (ms) |
| autoFocus | boolean | false | Whether to auto-focus the search box |
| className | string | - | custom style class name |
| style | React.CSSProperties | - | custom style |
| onKeywordChange | (keyword: string) => void | - | searchsearch keywords change callback'] |
| onSearchComplete | (results: Map<SearchType, SearchResult>) => void | - | search completed callback |
| onResultItemClick | (data: SearchResultItem, type: SearchType) => void | - | search result click callback |
| onError | (error: Error) => void | - | error callback |

###


---
*Source: [https://trtc.io/document/64706](https://trtc.io/document/64706)*
