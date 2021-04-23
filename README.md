# bind-rpz
Create Bind response policy zones from Adblock filter standard

[USAGE]

0) Configration if need you can :

Edit "ret_noerror" to change bind dns return => '0' for a NXDOMAIN return or '1' for a NOERROR
 
2) Generate the policy zone with :

python3 bind-rpz.py

3) Add in your bind configuration options (Generally /etc/bind/named.conf.options)

options {
response-policy { zone "banlist"; };
}

4) Add a zone where "file" path link to the generate file in step 2

zone "banlist" {
	type master;
	file "/etc/bind/db.banlist";
	allow-query {none;};
 };
 
