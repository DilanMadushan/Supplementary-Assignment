------------ORM  Supplementary  Assignment------------------

1. Query query = session.createQuery("FROM Book b WHERE b.publicationYear >2010");
   List student = query.list();

2. Query query = session.createQuery("update Book b set b.price = b.price + b.price * 10/100 where b.author.id = :authorId");
   query.setParameter("authorId",1); 
   System.out.println(query.executeUpdate());

3. public static boolean deleteAuthor(int id){

   Session session = FactoryConfiguration.getInstance().getSession();
   Transaction transaction = session.beginTransaction();

    Query query = session.createQuery("delete from Author a where id =: authorId ");
    query.setParameter("authorId",id);
    boolean isUpdated = query.executeUpdate()>0;

    transaction.commit();
    session.close();
    return isUpdated;

   }

4.  Query query = session.createQuery("select avg(b.price) from Book b");
    System.out.println(query.uniqueResult());

5.  Query query = session.createQuery("select author.name ,count(book) from Book as book join book.author as author group by author.name");
    List<Objects[]> list = query.list();

    for (Object[] obj: list) {
            System.out.println(obj[0]);
            System.out.println(obj[1]);
        }

6.  Query query = session.createQuery("SELECT book.title FROM Book book JOIN book.author author WHERE author.country = :country");
    query.setParameter("country", "America");
    System.out.println(query.list());

7.  in the project

8. Query query = session.createQuery("SELECT book.title FROM Book book WHERE book.price = (SELECT AVG(book.price) FROM Book book)");
   List list = query.list();
   System.out.println(list);


// table values

    Book book1 = new Book();
    book1.setTitle("Marvel1");
    book1.setPublicationYear(2000);
    book1.setPrice(1000);

    Book book2 = new Book();
    book2.setTitle("Marvel2");
    book2.setPublicationYear(2005);
    book2.setPrice(3000);

    Book book3 = new Book();
    book3.setTitle("Marvel3");
    book3.setPublicationYear(2015);
    book3.setPrice(5000);

    ArrayList<Book> books = new ArrayList<>();
    books.add(book1);
    books.add(book2);
    books.add(book3);

    Author author = new Author();
    author.setName("Kasun");
    author.setBookList(books);

    book1.setAuthor(author);
    book2.setAuthor(author);
    book3.setAuthor(author);

    session.save(book1);
    session.save(book2);
    session.save(book3);

    session.save(author);

///////////////////////////////////////////////////////////

    Book book1 = new Book();
    book1.setTitle("DC1");
    book1.setPublicationYear(2000);
    book1.setPrice(1000);

    Book book2 = new Book();
    book2.setTitle("DC2");
    book2.setPublicationYear(2005);
    book2.setPrice(3000);

    Book book3 = new Book();
    book3.setTitle("DC3");
    book3.setPublicationYear(2015);
    book3.setPrice(5000);

    ArrayList<Book> books = new ArrayList<>();
    books.add(book1);
    books.add(book2);
    books.add(book3);

    Author author = new Author();
    author.setName("Lahiru");
    author.setBookList(books);

    book1.setAuthor(author);
    book2.setAuthor(author);
    book3.setAuthor(author);

    session.save(book1);
    session.save(book2);
    session.save(book3);

    session.save(author);

//////////////////////////////////////////////////////////////////

