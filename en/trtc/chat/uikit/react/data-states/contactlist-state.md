# ContactList State

`ContactListState` is a relationship chain management hook based on Zustand, providing complete data management capability for the `ContactList` component. It supports friend list, group list, blocklist, application management, and other features. If custom component capacity cannot support your business, you can use `ContactListState` to implement your needs.

### Data

| Attribute Name | Type | Description |
| --- | --- | --- |
| friendList | Friend[] | friend list |
| groupList | Group[] | group list |
| blackList | UserProfile[] | blocklist |
| friendApplicationUnreadCount | number | Unread friend request quantity |
| friendGroupList | FriendGroup[] | friend group list |
| friendApplicationList | FriendApplication[] | friend request list |
| groupApplicationList | GroupApplication[] | Group Application List |

### Operation Method

| Attribute Name | Type | Description |
| --- | --- | --- |
| addFriend | (options: AddFriendParams) => Promise | Add a friend |
| deleteFriend | (options: DeleteFriendParams) => Promise | Remove friend |
| setFriendRemark | (options: FriendRemarkParams) => Promise | Set friend remark |
| markFriendApplicationAsRead | () => Promise | Mark friend request as read |
| acceptFriendApplication | (options: FriendApplicationParams) => Promise | Accept friend request |
| refuseFriendApplication | (userID: string) => Promise | Refuse friend application |
| addToBlacklist | (userIDList: string[]) => Promise | Add to blocklist |
| removeFromBlacklist | (userIDList: string[]) => Promise | Remove from blocklist |
| createFriendGroup | (options: FriendGroupParams) => Promise | create friend group |
| deleteFriendGroup | (name: string) => Promise | delete friend group |
| addToFriendGroup | (options: FriendGroupParams) => Promise | Add a friend to a group |
| removeFromFriendGroup | (options: FriendGroupParams) => Promise | Remove a friend from a group |
| renameFriendGroup | (options: RenameFriendGroupParams) => Promise | Rename friend group |
| joinGroup | (options: JoinGroupParams) => Promise | Request to join a group |
| acceptGroupApplication | (options: GroupApplicationParams) => Promise | Accept group request |
| refuseGroupApplication | (options: GroupApplicationParams) => Promise | Refuse group application |

## Usage Examples

```
friendList
```


---
*Source: [https://trtc.io/document/72204](https://trtc.io/document/72204)*
