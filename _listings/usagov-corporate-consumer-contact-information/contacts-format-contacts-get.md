---
swagger: "2.0"
info:
  title: USA.Gov Corporate Consumer Contact Information API
  description: We make the Corporate Consumer Contact listing found in the Consumer
    Action Handbook (PDF) available via a REST API. The API programmatically returns
    all of the information contained in the directory, or you can query the API to
    return just a subset of the available information.
  termsOfService: https://github.com/usagov/Corporate-Consumer-Contact-API-Documentation#terms-of-service
  contact:
    name: USA.Gov Developers
    email: usagov-developers@gsa.gov
  version: 1.0.0
host: www.usa.gov
basePath: api/USAGovAPI/
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /contacts.{format}/contacts:
    get:
      summary: Get Contacts
      description: Contacts is a general purpose call that, by default, will return
        all of the corporate directory records
      operationId: getContacts
      parameters:
      - in: query
        name: query_filter
        description: Return only corporate directory records that meet the criteria
          you enter into this parameter
        type: string
        format: string
      - in: query
        name: result_filter
        description: Return only the fields listed here (separated by |) as opposed
          to every field in each directory record
        type: string
        format: string
      - in: query
        name: sort
        description: Allows you to specify the sort order of the returned agency directory
          records
        type: string
        format: string
      - in: header
        name: X-Range
        description: You can limit the results returned by the API by including an
          X-Range HTTP header in your GET request, with a value of items=x to y, where
          x is the lower limit and y is the upper limit of the results to be returned
        type: string
        format: string
      responses:
        200:
          description: Successful response
          schema:
            type: array
            items:
              $ref: '#/definitions/Contacts'
      tags:
      - contacts
definitions:
  Contacts:
    properties:
      Id:
        description: A unique identifier for each directory record
        type: string
      Name:
        description: The name of the corporation.
        type: string
      Description:
        description: Any notes about contacting the corporation.
        type: string
      Subdivision:
        description: Used for mailing letters to the corporation..
        type: string
      Street1:
        description: A first line of address information (such as the street address)
          for contacting the corporation.
        type: string
      Street2:
        description: A second line of address information for contacting the corporation.
        type: string
      City:
        description: The city of the corporations mailing address.
        type: string
      StateTer:
        description: The state of the corporations mailing address.
        type: string
      Zip:
        description: The postal zip code of the corporations mailing address.
        type: string
      Email:
        description: The e-mail address for contacting the corporation.
        type: string
x-collection-name: USA.Gov Corporate Consumer Contact Information
x-streamrank:
  polling_total_time_average: 0
  polling_size_download_average: 0
  streaming_total_time_average: 0
  streaming_size_download_average: 0
  change_yes: 0
  change_no: 0
  time_percentage: 0
  size_percentage: 0
  change_percentage: 0
  last_run: ""
  days_run: 0
  minute_run: 0
---