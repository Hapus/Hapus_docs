###Basic API documentation (REST)

##GET (Fetch account information)

**Method:** GET

**API Endpoint:** http://www.hapus.com/api

**Params:**

1. Username
1. API key (MD5 password)

**Return type:** JSON

**Return data:**

<table border=1 style="border-collapse: collapse" cellpadding=5>
	<thead>
		<tr>
			<th>HTTP return code</th>
			<th>Brief explanation</th>
			<th>Data returned</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>400: Bad request</td>
			<td>Missing parameters</td>
			<td>A list of missing fields</td>
		</tr>
		<tr>
			<td>401: Unauthorized</td>
			<td>Credentials do not match</td>
			<td>-</td>
		</tr>
		<tr>
			<td>200: Success</td>
			<td>Membership information</td>
			<td>
				1. Username<br/>
				2. Account created on<br/>
				3. Plan name<br/>
				4. Monthly limit (In raw HTML size; KB)<br/>
				5. Monthly limit used (In raw HTML size; KB)
			</td>
		</tr>
		
	</tbody>
</table>

##POST (Create a PDF)

**Method:** POST

**API Endpoint:** http://www.hapus.com/api

**Params:**

1. Username
1. API key (MD5 password)
1. Type (Possible values: URL, HTML)
1. Resource (Either the source HTML or source URL)

**Return type:** JSON/PDF

**Return data:**

<table border=1 style="border-collapse: collapse" cellpadding=5>
	<thead>
		<tr>
			<th>HTTP return code</th>
			<th>Brief explanation</th>
			<th>Data returned</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>400: Bad request</td>
			<td>Missing parameters</td>
			<td>A list of missing fields or fields with incorrect values (for example, type). We'll throw this error if:
				1. Any of the params are missing
				2. Type is not one of URL or HTML
				3. Resource is not a valid URL
			</td>
		</tr>
		<tr>
			<td>401: Unauthorized</td>
			<td>Credentials do not match</td>
			<td>-</td>
		</tr>
		<tr>
			<td>402: Payment required</td>
			<td>Monthly limit (size in KB) reached or exceeded</td>
			<td>
				1. Username<br/>
				2. Account created on<br/>
				3. Plan name<br/>
				4. Monthly limit (In raw HTML size; KB)<br/>
				5. Monthly limit used (In raw HTML size; KB)
			</td>
		</tr>
		<tr>
			<td>413: HTML size too large</td>
			<td>The size of the HTML being asked to generate exceeds the membership type's size limit.</td>
			<td>-</td>
		</tr>
		<tr>
			<td>200: Success</td>
			<td>PDF generated</td>
			<td>
				We return the generated PDF. See [here](http://stackoverflow.com/a/2186644) for an explanation of how to do this.
			</td>
		</tr>
	</tbody>
</table>