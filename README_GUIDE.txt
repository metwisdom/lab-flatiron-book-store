FLATBOOKS BOOKSTORE LAB - README GUIDE
======================================

This guide follows the project README in order. The bookStore object and its
book data are already defined near the top of index.js. Add your JavaScript
solution below the comment that says "Write your code here!".


1. SETUP
--------
Install the project dependencies from the project folder:

    npm install

Run the automated tests after making changes:

    npm test

The tests check the page heading and that the book list contains book titles,
authors, and image URLs.


2. UPDATE THE EXISTING TITLE
----------------------------
The store name is stored in bookStore.name. Select the HTML element whose id
is "header", then set its textContent to that name.

HTML example:

    <h1 id="header">Store name goes here</h1>

JavaScript example:

    const bookStoreTitle = document.getElementById("header");
    bookStoreTitle.textContent = bookStore.name;

After this runs, the heading reads "Flatbooks Technical Books".


3. CREATE AN ELEMENT FOR EACH BOOK
----------------------------------
The books are in the array bookStore.books. Use forEach to run the same steps
once per book. The callback's book variable represents the current book.

For each book:

  a. Create an li to hold the book information.
  b. Create an h3 and set its textContent to the book title.
  c. Create a p and set its textContent to the book author.
  d. Create an img and set its src to the book imageUrl.
  e. Append the title, author, and image to the li.
  f. Append the li to the element whose id is "book-list".

HTML example:

    <ul id="book-list"></ul>

JavaScript example:

    const bookList = document.getElementById("book-list");

    bookStore.books.forEach((book) => {
      const bookContainer = document.createElement("li");

      const bookTitle = document.createElement("h3");
      bookTitle.textContent = book.title;

      const bookAuthor = document.createElement("p");
      bookAuthor.textContent = book.author;

      const bookImage = document.createElement("img");
      bookImage.src = book.imageUrl;

      bookContainer.append(bookTitle, bookAuthor, bookImage);
      bookList.append(bookContainer);
    });

The append calls place the elements inside their parent. The result is one li
per book, with that book's title, author, and cover image inside it.


4. BONUS: DELETE AN ELEMENT
---------------------------
To remove the element with id "delete-this", first select it and then call
remove() on it.

HTML example:

    <p id="delete-this">This element will be removed.</p>

JavaScript example:

    const elementToDelete = document.getElementById("delete-this");
    elementToDelete.remove();

Only include this code if the element exists in your HTML. Calling remove()
removes the selected element from the page.


5. THE README'S REMOVAL METHODS
-------------------------------
The README also shows two ways to remove an element.

Method A: remove a child from its parent with removeChild(). You must have
references to both the parent and the child:

    const list = document.querySelector("ul");
    const secondBook = list.querySelector("li:nth-child(2)");
    list.removeChild(secondBook);

Method B: call remove() directly on the element you want to remove:

    secondBook.remove();

Both examples remove an element from the DOM. For this lab's delete-this
bonus, the direct remove() method is the simplest choice.


HTML STRUCTURE EXAMPLE
----------------------
The README refers to these IDs. Make sure your index.html contains them:

    <h1 id="header"></h1>
    <ul id="book-list"></ul>
    <p id="delete-this">Remove me for the bonus challenge.</p>

The delete-this paragraph is optional unless you are completing the bonus.
