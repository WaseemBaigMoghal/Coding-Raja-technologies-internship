# Coding-Raja-technologies-internship
import mysql.connector
class LibraryManagementSystem:
    def __init__(self):
        self.conn = mysql.connector.connect(
            host="localhost",
            user="root",
            password="",
            database="library_management_system"
        )
        self.cursor = self.conn.cursor()
    def add_book(self, title, author, genre):
        self.cursor.execute("INSERT INTO books (title, author, genre) VALUES (%s, %s, %s)", (title, author, genre))
        self.conn.commit()
    def get_all_books(self):
        self.cursor.execute("SELECT * FROM books")
        return self.cursor.fetchall()
    def get_book_by_id(self, book_id):
        self.cursor.execute("SELECT * FROM books WHERE book_id = %s", (book_id,))
        return self.cursor.fetchone()
    def update_book(self, book_id, title, author, genre):
        self.cursor.execute("UPDATE books SET title = %s, author = %s, genre = %s WHERE book_id = %s", (title, author, genre, book_id))
        self.conn.commit()
    def delete_book(self, book_id):
        self.cursor.execute("DELETE FROM books WHERE book_id = %s", (book_id,))
        self.conn.commit()
    def add_patron(self, name, contact_info):
        self.cursor.execute("INSERT INTO patrons (name, contact_info) VALUES (%s, %s)", (name, contact_info))
        self.conn.commit()
    def get_all_patrons(self):
        self.cursor.execute("SELECT * FROM patrons")
        return self.cursor.fetchall()
    def get_patron_by_id(self, patron_id):
        self.cursor.execute("SELECT * FROM patrons WHERE patron_id = %s", (patron_id,))
        return self.cursor.fetchone()
    def update_patron(self, patron_id, name, contact_info):
        self.cursor.execute("UPDATE patrons SET name = %s, contact_info = %
