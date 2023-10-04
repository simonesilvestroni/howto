# Spotlight tips

## Search using the operators= AND, OR, NOT

You can narrow search results using Boolean operators (AND, OR, and NOT).  You can also use a minus sign (–), which means AND NOT, to exclude items when you search.

Here are examples of what you might type in a search field when you use Boolean operators:

- *author:tom OR author:thom* searches for items authored by Tom or Thom, if you don’t know the exact spelling of his name.
- *trip -france* searches for items that contain the word “trip” but not “france,” so  results might include photos from a trip to Spain but not to France.
- *kind:message date:6/29/21-7/25/21 NOT date:7/14/21* searches for email messages dated from 6/29/21 through 7/25/21, but excludes those dated 7/14/21.

## Search Specific Kinds of Files

For times when you want to find a particular file type on your Mac, Spotlight Search offers the option to modify search parameters to increase your chances of finding the correct file. You can do this by typing out the file name and appending “kind: format_type”. For example, if you want to look for a PDF file with the name “sample”, you will enter `sample kind: pdf` to find the particular file.

## Search items using natural language

Spotlight Search supports natural language search, which relies on algorithms to make sense of the words (in your queries) in the right context and serve you with relevant results accordingly. Using natural language, you can look up a lot of different items on your Mac.

For example, you can type “unread emails” to view all your unread emails, query “photos from march” to find all the photos (including screenshots) from the month of March, or type “documents I created yesterday” to view all the documents you created yesterday — the scope of use is limitless.

A few uses of natural language:

- Find the latest match score of your favorite team/club: type the name of a team to find its score update. `Eg: man utd vs liverpool`
- Find the weather at your location: enter weather city_name to find the current weather situation of that place.
`Eg: weather mumbai`
- Find an article/video on a website/YouTube: type your query explaining what you are looking for and on which website. `Eg: best gan chargers techpp`
- Find live price updates for a stock: enter the ticker symbol of the company stock of which you want to know the price.
`Eg: TSLA`
- Find nearby shops/eateries/theatres: look up nearby shops/eateries/theatres etc. in your locality.
`Eg: theatres near me`

## Shortcuts

| Shortcut                                         | Action                                                       |
| ------------------------------------------------ | ------------------------------------------------------------ |
| **Return**                                       | Open a result                                                |
| Hold the **Command key** on a file/folder result | Shows the complete path in Finder                            |
| **⌘ + B**                                        | Look it up on the internet using the default search engine on your Mac’s primary (default) browser |
| **⌘ + R**                                        | Open a file in an app or Finder                              |
| **⌘ + ⌥ + space**                                | Open a Finder window with the selected search field          |
| **Tab**                                          | View the preview area                                        |
| **↑**                                            | Move to the previous result                                  |
| **↓**                                            | Move to the next result                                      |
| **⌘ + ↑**                                        | Move to the first result in the category                     |
| **⌘ + ↓**                                        | Move to the last result in the category                      |
| **⌘ + L**                                        | Go to the first available Dictionary definition              |

## Narrow a search

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

There are several other keywords that you can use to find items, such as from, to, author, with, by, tag, title, name, keyword, and contains. To use a keyword, enter it followed by a colon, then enter your search  term. For example, enter “author:John” or “title:New York City.”

## In a Terminal

Finds only matching filenames (instead of all files that contain the search text):

```bash
mdfind -name
```

### Reset index

Turn Spotlight **off**:

```bash
sudo mdutil -a -i off
```

Then:

```bash
sudo mdutil -E /
sudo rm -Rf /var/folders/*
```

After a reboot, turn Spotlight **back on**:

```bash
sudo mdutil -a -i on
```

See the progress:

```bash
sudo opensnoop -n mdworker
```

Turn indexing **off** for pure backup disks:

```bash
sudo mdutil -i off /Mountpoint/Volumename
```

---

#macOS #Bash #CommandLine