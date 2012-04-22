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
			<td>200: Payment required</td>
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

