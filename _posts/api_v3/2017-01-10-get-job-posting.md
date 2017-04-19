---
category: API v3
title: 'Getting Job Posting'
type: 'GET'
api_path: '/job_postings'

layout: default
---

### Request

Get all Job Postings.

```
GET /job_postings.json
Authorization: Basic <base64 encoded token> 
X-API-Version: 3.0.0
```

### Response

```
Status: 200 OK
Content-Type: application/json
```

```
[
	{
		"id": 3,
		"title": "Account Manager",
		"teaser": "The Account Manager serves as the primary business contact for the client and is responsible for client satisfaction. The AM is expected to consistently provide excellent customer service to accounts, as well as represent client needs and goals within the organization to ensure quality. In addition, the AM will should build relationships with clients to encourage new and repeat business opportunities.\r\nResponsibilities:...",
		"positions": 1,
		"public": false,
		"closed": false,
		"created": "2012-11-19T16:00:02+00:00",
		"url": "/job_postings/3.json"
	}, 
	{
		"id": 4,
		"title": "Human Resources Assistant",
		"teaser": "The Human Resources assistant assists with the administration of the day-to-day operations of the human resources functions and duties. The HR assistant carries out responsibilities in some or all of the following functional areas: departmental development, HRIS, employee relations, training and development, benefits, compensation, organization development, executive administration, and employment.\nThe HR assistant has partial responsibility for these areas:\n\nrecruiting and staffing logistics;...",
		"positions": 1,
		"public": false,
		"closed": false,
		"created": "2012-11-19T16:00:07+00:00",
		"url": "/job_postings/4.json"
	},
	{
		"id": 2,
		"title": "Sales Engineer",
		"teaser": "Sales Engineers are the primary technical resource for the field sales force. Sales Engineers are responsible for actively driving and managing the technology evaluation stage of the sales process, working in conjunction with the sales team as the key technical advisor and product advocate for our products. The Sales Engineer must be able to articulate technology and product positioning to both business and technical users. Must be able to identify all technical issues of assigned accounts to as...",
		"positions": 1,
		"public": false,
		"closed": false,
		"created": "2012-11-19T15:59:57+00:00",
		"url": "/job_postings/2.json"
	},
	{
		"id": 1,
		"title": "UX Designer",
		"teaser": "Job Description\nUser-experience designers are responsible for creating the look and feel of a specific&nbsp;computer&nbsp;interface. This allows them to navigate the functionality of that interface and produce a certain type of human-computer interaction. These designers generally work on teams, applying their skills to a website or computer product, such as a piece of software. These teams can include different types of designers....",
		"positions": 2,
		"public": false,
		"closed": false,
		"created": "2012-11-19T15:59:49+00:00",
		"url": "/job_postings/1.json"
	}
]
```

### Request

View details about an individual Job Posting.

Note that the **`description`** field is only HTML field, TribeHR doesn't use RichText format here.

```
GET /job_postings/{id}.json
Authorization: Basic <base64 encoded token> 
X-API-Version: 3.0.0
```

### Response

```
Status: 200 OK
Content-Type: application/json
```

```
{
	"id": 3,
	"title": "Account Manager",
	"description": "<p>The Account Manager serves as the primary business contact for the client and is responsible for client satisfaction. The AM is expected to consistently provide excellent customer service to accounts, as well as represent client needs and goals within the organization to ensure quality. In addition, the AM will should build relationships with clients to encourage new and repeat business opportunities.</p>\r\n<p><strong>Responsibilities:</strong></p>\r\n<ul>\r\n<li>Responsible for all client communications, conflict resolution, and compliance on client deliverables and revenue.</li>\r\n<li>Reviews all major deliverables (i.e. strategic brief, function spec, tech spec, etc.) to ensure quality standards and client expectations are met.</li>\r\n<li>Ensures that client issues are dealt with in an efficient manner, informing the Account Director or Managing Director of any problems that may arise.</li>\r\n<li>Owns the contract and contract renewals for new work for an existing client.</li>\r\n<li>Approves Change Orders and invoices, and is responsible for payment collections.</li>\r\n<li>Works closely with the project team in order to maintain a continuous knowledge of project status in order to identify potential issues and/or opportunities within or related to the project.</li>\r\n<li>Ensures that all processes and procedures are completed, quality standards are met, and that projects are profitable.</li>\r\n<li>Aware and in pursuit of opportunities for account growth and new business, involving the Account Director, Sales or other Q-Bridge support.</li>\r\n<li>Communicates the client's goals and represent the client's interests to the team.</li>\r\n<li>Provides regular two-way communication between the client and team, to provide strong team representation and set proper client expectations.</li>\r\n<li>Understanding of company capabilities and service, and effectively communicates all offerings to the client.</li>\r\n<li>Reports to the Account Director, providing regular input on all account activity, including status and call reports on a weekly basis.</li>\r\n</ul>\r\n<p><strong>Requirements:</strong></p>\r\n<ul>\r\n<li>Proven Account Management skills required in order to create, maintain and enhance customer relationships</li>\r\n<li>Minimum 3 years of Account/project management experience</li>\r\n<li>Extremely detail oriented</li>\r\n<li>Technical competence (understand software, hardware, networks, etc)</li>\r\n<li>Motivated, goal oriented, persistent and a skilled negotiator</li>\r\n<li>High level of initiative and work well in a team environment</li>\r\n<li>Excellent written and oral communication skills</li>\r\n<li>Handles stressful situations and deadline pressures well</li>\r\n<li>Plans and carries out responsibilities with minimal direction</li>\r\n<li>Undergraduate degree</li>\r\n</ul>\r\n<p>&nbsp;</p>",
	"teaser": "The Account Manager serves as the primary business contact for the client and is responsible for client satisfaction. The AM is expected to consistently provide excellent customer service to accounts, as well as represent client needs and goals within the organization to ensure quality. In addition, the AM will should build relationships with clients to encourage new and repeat business opportunities.\r\nResponsibilities:...",
	"close_date": "2013-05-31",
	"location_city": "New York",
	"location_state": "New York",
	"location_country": "US",
	"positions": 1,
	"public": false,
	"closed": false,
	"eeo_enabled": true,
	"created": "2012-11-19T16:00:02+00:00",
	"modified": "2017-03-23T15:52:28+00:00",
	"url": "/job_postings/3.json",
	"job": {
		"id": 1,
		"title": "Account Manager",
		"url": "/jobs/1.json"
	},
	"department": {
		"id": 2,
		"name": "Sales & Marketing",
		"url": "/departments/2.json"
	},
	"location": {
		"id": 2,
		"name": "Corporate Office [Headquarters]",
		"url": "/locations/2.json"
	},
	"applications": null,
	"reviewers": [
		{
			"id": "10",
			"username": "Carlene",
			"avatar": {
				"url": "/attachments/view/User/avatar/10"
			},
			"email": "FakeEmail+4@ribbitco.biz",
			"display_name": "Carlene Hail",
			"url": "/users/10.json"
		},
		{
			"id": "17",
			"username": "Milagros",
			"avatar": {
				"url": "/attachments/view/User/avatar/17"
			},
			"email": "FakeEmail+7@ribbitco.biz",
			"display_name": "Milagros Melnyk",
			"url": "/users/17.json"
		},
		{
			"id": "12",
			"username": "JessieP",
			"avatar": {
				"url": "/attachments/view/User/avatar/12"
			},
			"email": "FakeEmail+2@ribbitco.biz",
			"display_name": "Jessie Prue",
			"url": "/users/12.json"
		},
		{
			"id": "13",
			"username": "MonicaB",
			"avatar": {
				"url": "/attachments/view/User/avatar/13"
			},
			"email": "FakeEmail+5@ribbitco.biz",
			"display_name": "Monica Bolenbaugh",
			"url": "/users/13.json"
		}
	]
}
```