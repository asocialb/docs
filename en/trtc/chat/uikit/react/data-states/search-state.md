# Search State

SearchState is a search state management hook based on Zustand, providing complete status management capacity for the Search component. It supports various search modes (standard mode, embedded mode) and manages search keywords, search results, loading status, error handling, and other features. If the customize component power cannot support your business, you can use SearchState to implement your needs.

#### Data

| Attribute Name | Type | Description |
| --- | --- | --- |
| keyword | string | current search keyword |
| results | Map<SearchType, SearchResult<SearchType>> | search result set |
| isLoading | boolean | whether searching |
| error | Error \| null | error information |
| searchAdvancedParams | Map<ISearchType, SearchParamsMap[SearchType]> | Advanced search parameters |
| selectedSearchType | SearchType \| 'all' | Current search type |

#### Operation Method

| Method Name | Type | Description |
| --- | --- | --- |
| setKeyword | (k: string) => void | Set search keyword |
| loadMore | (type?: SearchType) => Promise<void> | Load more search results |
| setSelectedType | (type: SearchType \| 'all') => void | Set search type |
| setSearchMessageAdvancedParams | (params: SearchCloudMessagesParams) => void | Set advanced message search parameters |
| setSearchUserAdvancedParams | (params: SearchCloudUsersParams) => void | Set advanced user search parameters |
| setSearchGroupAdvancedParams | (params: SearchCloudGroupsParams) => void | Set advanced group search parameters |

## Usage Examples

```
import { useSearchState, VariantType } from '@tencentcloud/chat-uikit-react';const {    keyword,    results,    isLoading,    error,    setKeyword,    setSelectedType,    loadMore  } = useSearchState(VariantType.STANDARD);
```

##


---
*Source: [https://trtc.io/document/72092](https://trtc.io/document/72092)*
