# Search

## Component Overview

Search is a complete search solution with a full set of components, including search bar, result display, advanced search, and other features. It is suitable for user, group, and message search in instant messaging, online meeting, and online education scenarios.

> **Note:**Note: This feature belongs to VAS. You need to purchase cloud search plugin. Please click [purchase](https://console.trtc.io/chat/plugin/TUICloudSearch).

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/d66ac806621811f091585254001c06ec.png)

## Component Architecture

```
Search (main component)âââ SearchBar              # Search bar componentâââ SearchResults          # Search result componentâââ SearchAdvanced         # Advanced search componentâââ SearchResultsItem      # Search result item component    âââ User               # User result item    âââ Group              # Group result item    âââ Message            # Message result item    âââ Conversation       # Session result item
```

## Search Mode

| **Mini Mode** | **Standard Mode** | **Embedded Mode** |
| --- | --- | --- |
| Suitable for sidebar or small containerDisplay finite number of resultsSupport expand to view more | Suitable for full-screen search UIFeature demonstrationAdvanced Search Support | Suitable for chat UIFocus on message searchOptimized layout |
|  ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/9041fa01622911f0b324525400e889b2.png) |  ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/2019d8cc622a11f0bac1525400454e06.png) |  ![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/eeff790f622911f091585254001c06ec.png) |

## Props

| Attribute Name | Type | Default Value | Description |
| --- | --- | --- | --- |
| variant | VariantType | VariantType.MINI | Search mode: mini, standard, embedded |
| SearchBar | React.ComponentType<SearchBarProps> | DefaultSearchBar | Custom search box component |
| SearchResults | React.ComponentType<SearchResultsProps> | DefaultSearchResults | Custom search result component |
| SearchAdvanced | React.ComponentType<SearchAdvancedProps> | DefaultSearchAdvanced | Custom advanced search component |
| SearchResultsPresearch | React.ComponentType | - | Search placeholder component |
| SearchResultsLoading | React.ComponentType | - | Loading placeholder component |
| SearchResultsEmpty | React.ComponentType | - | Empty result placeholder component |
| SearchResultItem | React.ComponentType<ResultItemProps> | - | Custom search result item component |
| debounceTime | number | 300 | Search debounce time (ms) |
| autoFocus | boolean | false | Auto-focus search box |
| className | string | - | Custom style class name |
| style | React.CSSProperties | - | custom style |
| onKeywordChange | (keyword: string) => void | - | search keyword change callback |
| onSearchComplete | (results: Map<SearchType, SearchResult>) => void | - | search complete callback |
| onResultItemClick | (data: SearchResultItem, type: SearchType) => void | - | search result click callback |
| onError | (error: Error) => void | - | search error callback |

## Basic Usage

```
import { Search, VariantType } from '@tencentcloud/chat-uikit-react';function App() {  return (    <Search      variant={VariantType.STANDARD}      onResultItemClick={(data, type) => {        console.log('Search result click:', data, type);      }}    />  );}
```

## Custom Capabilities

`Search` provides users with various and dimensional Props APIs, allowing them to customize features, UI, and modules.

`Search` component provides multiple replaceable subcomponents, allowing users to customize `SearchBar`, `SearchResults`, `SearchAdvanced`, `SearchResultItem`, `SearchResultsPresearch`, `SearchResultsLoading`, `SearchResultsEmpty`. Users can also leverage default subcomponents for secondary development customization.

Custom SearchBar

Custom Search Results

Custom Search Advanced

Custom Search Result Item

Custom Placeholder Component

**Props**

| Attribute Name | Type | Default Value | Description |
| --- | --- | --- | --- |
| data | SearchResultItem | - | search result data |
| type | SearchType | - | search result type |
| keyword | string | - | search keyword |
| onClick | (data: SearchResultItem, type: SearchType) => void | - | click callback |
| className | string | - | Custom style class name |

**Example**

```
const CustomSearchBar = ({ value, onChange, onClear, placeholder }) => (  <div className="custom-search-bar">    <input      type="text"      value={value}      onChange={onChange}      placeholder={placeholder}    />    {value && <button onClick={onClear}>Clear</button>}  </div>);<Search SearchBar={CustomSearchBar} />
```

**Props**

| Attribute Name | Type | Default Value | Description |
| --- | --- | --- | --- |
| results | `Map<SearchType, SearchResult>` | - | search result data |
| isLoading | `boolean` | - | whether loading |
| error | `Error \| null` | - | Error Message |
| keyword | `string` | - | search keyword |
| typeLabels | `Record<SearchType, string>` | - | search type tag |
| onLoadMore | `(type: SearchType) => void` | - | Load more callback |
| onResultItemClick | `(data: SearchResultItem, type: SearchType) => void` | - | result item click callback |
| SearchResultsLoading | `React.ComponentType` | `Loading` | Custom load component |
| SearchResultsPresearch | `React.ComponentType` | - | Search placeholder component |
| SearchResultsEmpty | `React.ComponentType` | `EmptyResult` | Empty result placeholder component |
| SearchResultItem | `React.ComponentType<ResultItemProps>` | `DefaultSearchResultsItem` | Custom result item component |
| variant | `VariantType` | `VariantType.STANDARD` | Display Mode |
| searchType | `SearchType \| 'all'` | `'all'` | Current search type |

**Example**

```
const CustomSearchResults = ({ results, keyword, onResultItemClick }) => (  <div className="custom-results">    {Array.from(results.entries()).map(([type, result]) => (      <div key={type}>        <h3>{type}</h3>        {result.resultList.map((item, index) => (          <div key={index} onClick={() => onResultItemClick(item, type)}>            {/* Custom result item */}          </div>        ))}      </div>    ))}  </div>);<Search SearchResults={CustomSearchResults} />
```

**Props**

| Attribute Name | Type | Default Value | Description |
| --- | --- | --- | --- |
| variant | `VariantType` | - | Display Mode |
| searchType | `SearchTabType` | - | Current search type |
| advancedParams | `Map<SearchType, SearchParamsMap[SearchType]>` | - | Advanced search parameters |
| onAdvancedParamsChange | `(type: SearchType, params: SearchParamsMap[SearchType]) => void` | - | Parameter change callback |

**Example**

```
SearchAdvanced
```

**Props**

| Attribute Name | Type | Default Value | Description |
| --- | --- | --- | --- |
| data | `SearchResultItem` | - | search result data |
| type | `SearchType` | - | search result type |
| keyword | `string` | - | search keyword |
| onClick | `(data: SearchResultItem, type: SearchType) => void` | - | click callback |
| className | `string` | - | Custom style class name |

**Example**

```
SearchResultItem
```

**Props**

| Attribute Name | Type | Default Value | Description |
| --- | --- | --- | --- |
| SearchResultsPresearch | `React.ComponentType` | - | Search placeholder component |
| SearchResultsLoading | `React.ComponentType` | - | Loading placeholder component |
| SearchResultsEmpty | `React.ComponentType` | - | Empty result placeholder component |

**Example**

```
<Search  SearchResultsPresearch={() => <div>Enter keywords to start search</div>}  SearchResultsLoading={() => <div>Searching...</div>}  SearchResultsEmpty={() => <div>No result found</div>}/>
```

## FAQs

### How to Customize the Search Result Display Format

A: Use the `SearchResultItem` property to import a customize component.

### How to Handle Search Performance Issues

A: Adjust `debounceTime`, use React.memo, and consider result cache.

### How to Optimize Mobile Terminal

A: The component automatically adapts to mobile terminals and can be further customized via CSS.

### How to Support Multilingual

A: The component has built-in internationalization support. Use `useUIKit` to get translations.


---
*Source: [https://trtc.io/document/72091](https://trtc.io/document/72091)*
