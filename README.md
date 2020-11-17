# Node.js PostgreSQL CRUD Example Express RestAPIs + Sequelize + PostgreSQL tutorial

Tutorial Link : [Nodejs PostgreSQL CRUD Example](https://loizenai.com/node-js-postgresql-crud-example/)

![Nodejs PostgreSQL CRUD Example](https://loizenai.com/wp-content/uploads/2020/08/Node.js-PostgreSQL-CRUD-Example-Express-RestAPIs.png)

In the tutorial, I will introduce step by step how to create a ‘Node.js PostgreSQL CRUD Example – Express RestAPIs + Sequelize + PostgreSQL tutorial’ with a full-stack technologies: Express RestAPI Framework (Cors + Body-Parse) + Sequelize ORM + PostgreSQL database.

## Overview Architecture – Node.js Express Sequelize PostgreSQL CRUD RestAPIs Example

![Overview Architecture – Node.js Express Sequelize PostgreSQL CRUD RestAPIs Example](https://loizenai.com/wp-content/uploads/2020/08/Nodejs-PostgreSQL-CRUD-Example-Architecture-Overview.png)

To handling all POST/GET/PUT/DELETE RestAPI requests and do CRUD with PostgreSQL database, we create a backend web Node.js application with 4 main points:

- To handle CRUD RestAPI requests with Node.js, we use Express.js framework.
- To do CRUD operations with PostgreSQL database, we use Sequelize ORM queries.
- We define all RestAPI urls in router.js.
- We implement how to process each RestAPI requests in controller.js file.

## Project Goal

After the tutorial, we will understand overall architecture and clearly picture how to create a full backend web restapis application with Node.js technology from abstract overview to specific helpful frameworks and details sourcecode for connecting all things in one application.

We will define 8 RestAPIs with POST/GET/PUT/DELETE methods for posting, fetching, updating, removing, pagination, filtering and sorting data from PostgreSQL database:

– For normally requests with POST/GET/PUT/DELETE methods, we create a first GROUP with 5 RestAPIs:

1. POST RestAPI /api/customers/create will handle the submit data from client to save in PostgreSQL database
2. GET RestAPI /api/customers/all will fetch all data from PostgreSQL database
3. GET RestAPI /api/customers/onebyid/:id will get a single data by primary key id
4. PUT RestAPI /api/customers/update/:id will update an existed record in PostgreSQL database
5. DELETE RestAPI /api/customers/delete/:id will delete an existed record in PostgreSQL which is associated with a primary key id

– For advanced purpose such as Filtering, Pagination and Sorting, we create the second RestAPIs group:

1.Filtering Request – GET RestAPI /api/customers/filteringbyage is used to fetch all records from PostgreSQL with a filtering by age
2.Pagination Request – GET RestAPI /api/customers/pagination is used to fetch data from PostgreSQL with pagination purpose.
3. Pagination Filtering and Sorting – GET RestAPI /api/customers/pagefiltersort is defined to fetch data from PostgreSQL with pagination, filtering by age and ordering by 2 fields firstname and lastname

### Testcase 1 – Nodejs Express PostgreSQL POST Request

![Testcase 1 – Nodejs Express PostgreSQL POST Request](https://loizenai.com/wp-content/uploads/2020/08/testcase-1-nodejs-postgresql-crud-post-request.png)

Check PostgreSQL’s records:

![Check PostgreSQL database records](https://loizenai.com/wp-content/uploads/2020/08/Check-PostgreSQL-database-records.png)

### Testcase 2 – Nodejs Express PostgreSQL GET Request: get all data from PostgreSQL

![Testcase 2 – Nodejs Express PostgreSQL GET Request: get all data from PostgreSQL](https://loizenai.com/wp-content/uploads/2020/08/Testcase-2-Nodejs-GET-request-Retrieve-all-records-from-PostgreSQL.png)

### Testcase 3 – Nodejs Express PostgreSQL GET Request: get one data record from PostgreSQL with a given id

![Testcase 3 – Nodejs Express PostgreSQL GET Request: get one data record from PostgreSQL with a given id](https://loizenai.com/wp-content/uploads/2020/08/Testcase-3-GET-request-retrieve-a-Customer-by-a-given-ID.png)

### Testcase 4 – Nodejs Express PostgreSQL UPDATE request

![Testcase 4 – Nodejs Express PostgreSQL UPDATE request](https://loizenai.com/wp-content/uploads/2020/08/Testcase-4-Nodejs-PUT-request-Update-a-Customer-data-by-given-ID-to-PostgreSQL-database.png)

### Testcase 5 – Nodejs Express PostgreSQL DELETE request: delete a record with a given id

![Testcase 5 – Nodejs Express PostgreSQL DELETE request: delete a record with a given id](https://loizenai.com/wp-content/uploads/2020/08/Testcase-5-Nodejs-Delete-request-Delete-a-Customer-by-given-ID-from-PostgreSQL-database.png)

### Testcase 6 – Nodejs Express PostgreSQL Filtering request by a field

![Testcase 6 – Nodejs Express PostgreSQL Filtering request by a field](https://loizenai.com/wp-content/uploads/2020/08/Testcase-6-Filtering-Customer-by-Age-from-PostgreSQL-database.png)

### Testcase 7 – Nodejs Express PostgreSQL Pagination request

![Testcase 7 – Nodejs Express PostgreSQL Pagination request](https://loizenai.com/wp-content/uploads/2020/08/Testcase-7-Nodejs-do-a-Pagination-Request-from-PostgreSQL-database.png)

What does it mean? We had done a pagination request to fetch a second page page = 1 with a size of page is 7 (limit=7)

The RestAPI returns a json result with useful informantion as below:

1. totalItems describes the number of records in database
2. totalPages describes the total number of pages with requested limit
3. limit describes the number of items for a fetching page
4. currentPageNumber is the order number of requested page (currentPageNumber = page + 1)
5. currentPageSize is the size of the current page (currentPageSize <= limit)
6. customers is a dataset attached with the pagination request

Using Native PostgreSQL query with LIMIT statement to check the above result:

![Check the Pagination using Native PostgreSQL Query with Offset & Limit Statement](https://loizenai.com/wp-content/uploads/2020/08/Check-the-Pagination-using-Native-PostgreSQL-Query-with-Offset-Limit-Statement.png)

### Testcase 8 - Nodejs Express PostgreSQL Pagination Filtering and Sorting request

![Testcase 8 - Nodejs Express PostgreSQL Pagination Filtering and Sorting request](https://loizenai.com/wp-content/uploads/2020/08/Testcase-8-Nodejs-RestAPI-PaginationFilteringSorting-PostgreSQL-database.png)

What does it mean? - The above request had done with 3 proccessing steps:

1. Do the Filtering with age=23, and We just have 4 Customer items in database having age is 23 so returned totalItems is 4. The totalPages is 2 because of 2 reason:
- limit: 3
- and totalPages = Math.ceil(data.count / limit) = Math.ceil(4 / 3)

![Check Filtering PostgreSQL records by Native Query](https://loizenai.com/wp-content/uploads/2020/08/Check-Filtering-PostgreSQL-records-by-Native-Query.png)

2. Do the pagination with offset = 0 (limit*page) and row_counts = 3:

![Check the Pagination using Native PostgreSQL Query with Offset & Limit Statement](https://loizenai.com/wp-content/uploads/2020/08/Check-the-Pagination-using-Native-PostgreSQL-Query-with-Offset-Limit-Statement-1.png)

3. Finally Do the Sorting by firstname with ascending order and lastname with descending order:

![PosgreSQL Pagination Filtering Sorting by Native Query](https://loizenai.com/wp-content/uploads/2020/08/PosgreSQL-Pagination-Filtering-Sorting-by-Native-Query.png)

## Related post

- [Angular 10 Node.js MySQL CRUD Example](https://loizenai.com/angular-10-node-js-mysql-crud-application-example-fullstack-tutorials-with-express-restapis-sequelize-orm/)
- [Token Based Authentication in Node.js using JWT (JSON Web Tokens) + MySQL Example](https://loizenai.com/nodejs-token-based-authentication-jwt-json-web-tokens-authentication-mysql-example/)
- [Nodejs RestAPIs Upload Download Multiple Excel Files](https://loizenai.com/nodejs-restapis-upload-download-multiple-excel-files-to-mysql-postgresql/)


