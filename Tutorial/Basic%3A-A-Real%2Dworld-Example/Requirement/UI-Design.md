There are 3 pages of the `Blocked Senders` feature.

- Blocked Senders: for listing blocked senders
- New Blocked Sender: for creating a blocked sender
- Edit Blocked Sender: for editing a blocked sender

# Blocked Senders

Since we might have multiple blocked senders, we need a UI to display the list of blocked senders.

![list.png](/.attachments/list-2aa7077c-876e-4013-bd63-911d1c1fcb03.png)

- Click the `New Blocked Sender` button to switch to the `New Blocked Sender` page.

- The checkbox column of the table is for selecting multiple rows and perform batch operations such as `Delete`. After selecting rows, the operation buttons will show up, which covering on top of the table header:
  ![image.png](/.attachments/image-7e7d5343-3e69-43e0-81fd-e713e791278e.png)

- For batch `Delete` operation

  - confirm before deleting
    ![image.png](/.attachments/image-b6de043f-ac7a-403e-9a38-7f0d6fc1e253.png)
  - a success message will show up after the delete operation.
    ![image.png](/.attachments/image-6a8a1262-0f63-433c-80ed-efe59bd9ef82.png)

- The `Email/Domain` column contains links to the `Edit Blocked Sender` page. Click it go to the `Edit Blocked Sender` page.
- The `Blocked Level` column display plain text
- The operations column contains icon buttons of operations such as `Edit` or `Delete` for each table row.
  - Click `Edit` icon go to the `Edit Blocked Sender` page. This is the same as clicking the `Email/Domain` link.
  - Click the `Delete` icon to remove the corresponding row. Before deleting a confirmation dialog will show up (similar to batch deleting) and display a success message after delete as well.

# New Blocked Sender

![new.png](/.attachments/new-171591d7-fa12-4fe4-8c3f-d321921cde03.png)

- Email/Domain validation failed:
  ![image.png](/.attachments/image-4300fa8d-f013-437b-9c41-11e77ae6b280.png)
  ![image.png](/.attachments/image-ffc87ff8-d4c8-46fd-8e17-b43c61d77b67.png)

- Click `Save` button to create a blcked sender and switch back to `Blocked Senders` page.
- Click `Cancel` button to discard current editing form and switch back to `Blocked Senders` page.

# Edit Blocked Sender

Edit page is the same as New Page except page title is `Edit Blocked Sender` and click `Save` button will update current blocked sender instead of creating one.
![edit.png](/.attachments/edit-5e728ca1-afa2-4abe-822a-b9e2711a1c1f.png)
