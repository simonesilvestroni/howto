# Spotlight: narrow a search

1. Start your search on your Mac in Spotlight or in a Finder window.

   - **In Spotlight**: Open Spotlight, enter your search term in the search field, then click Search in Finder at the bottom of the search results.

   - **In a Finder window**: Enter your search term in the search field, then press Return.

2. Click the Add button on the right side of the search window, below the search field.

3. Click the far-left pop-up menu, then choose or add search criteria.

   For example, to search for only a certain type of item instead of all items, choose Kind. Or to search for any item whose name contains a particular word or phrase, choose Name.

   To add criteria, choose Other, then select each attribute you want to add. For example, to search copyright information, select Copyright in the list of attributes, then click OK.
   
   ![](https://help.apple.com/assets/62A8ED2F99A5D0045E612A42/62A8ED3DCA32D1047032C8FF/en_US/95e76d2ecb826462b158c76989458a46.png)

4. Choose criteria from other pop-up menus that appear.

   For example, after you choose Kind, click the other pop-up menu to specify Document or Image. To add a kind, choose Other.

5. Add or remove search criteria as needed by clicking the Add button or the Remove button.

   To search using Boolean operators (OR, AND, or NOT), press and hold the Option key, then click the 3-dots button that appears. You can set criteria and specify that Any, All, or None of them must be met. 

## Search for metadata attributes

Most items contain metadata that describes the item contents, how it was  created, and other attributes. For example, when you take a digital  photo, information such as the camera model, the aperture, and the focal length are among the many attributes automatically stored in the file  as metadata. To view metadata for a file, select the file, then choose  File > Get Info.

Here are examples of how you might use metadata attributes in a search:

- *trip kind:document* searches for the word “trip” in documents only.
- *author:tom* searches for all items written by Tom.
- *kind:images created:8/16/21* searches for images created on a specific date.
- *kind:music by:“glenn miller”* searches for music by Glenn Miller.
- *modified:<=7/29/21* searches for items modified on or before a specific date.

## Search by the type of items

You can use keywords to specify the type of items you’re searching for, such as apps, contacts, or bookmarks.

To specify the type of item, add the text “kind:[*type of item*]” at the end of your search. For example, to search for photos of New  York City, enter “New York City kind:images.” To search for email  messages that mention Nisha, enter “Nisha kind:email.”

<br>

| Type of item    | Keyword                                                  |
| :-------------- | :------------------------------------------------------- |
| Apps            | kind:application kind:applicationskind:app               |
| Contacts        | kind:contactkind:contacts                                |
| Folders         | kind:folderkind:folders                                  |
| Email           | kind:emailkind:emailskind:mail messagekind:mail messages |
| Calendar events | kind:eventkind:events                                    |
| Reminders       | kind:reminderkind:reminders                              |
| Images          | kind:imagekind:images                                    |
| Movies          | kind:moviekind:movies                                    |
| Music           | kind:music                                               |
| Audio           | kind:audio                                               |
| PDF             | kind:pdfkind:pdfs                                        |
| Preferences     | kind:system preferenceskind:preferences                  |
| Bookmarks       | kind:bookmarkkind:bookmarks                              |
| Fonts           | kind:fontkind:fonts                                      |
| Presentations   | kind:presentationkind:presentations                      |

<br>

There are several other keywords that you can use to find items, such as from, to, author, with, by, tag, title, name, keyword, and contains. To use a keyword, enter it followed by a colon, then enter your search  term. For example, enter “author:John” or “title:New York City.”

## Search using AND, OR, and NOT

You can narrow search results using Boolean operators (AND, OR, and NOT).  You can also use a minus sign (–), which means AND NOT, to exclude items when you search.

Here are examples of what you might type in a search field when you use Boolean operators:

- *author:tom OR author:thom* searches for items authored by Tom or Thom, if you don’t know the exact spelling of his name.
- *trip -france* searches for items that contain the word “trip” but not “france,” so  results might include photos from a trip to Spain but not to France.
- *kind:message date:6/29/21-7/25/21 NOT date:7/14/21* searches for email messages dated from 6/29/21 through 7/25/21, but excludes those dated 7/14/21.

---

#macOS