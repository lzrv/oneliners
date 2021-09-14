# Oneliners

### Format a log saved as a single line
```bash
sed 's/[0-9]\{4\}-[0-9]\{2\}-[0-9]\{2\}/\n&/g' single_line.log > multi_line.log
```

Sed finds a date timestamp and prints it on a new line. It can format a log file that was saved as a single line and make it readable.

### Bash environment variables in cURL

```bash
curl 'https://'"$HUB"'/api/journal/projects/'"$PROJECTID"'/versions/'"$VERSIONID"'?offset=0&limit=50&sort=timestamp%20DESC'  -H 'Cookie: AUTHORIZATION_BEARER='"$AUTHORIZATION_BEARER" | jq | less
```

### Search and replace

```bash
sed -i 's/SEARCH_REGEX/REPLACEMENT/g' INPUTFILE
```

If there are slashes(/) in the search/replacement patterns(for example, if the search pattern contains a URL), for sed to work use a percent(%) sign as a delimiter.

An example - cleaning urls from urldefense to improve readability:

```bash
sed -i 's%<https://urldefense.com/v3/__%,%g' kb_discrepancy.txt
```



```bash
sed -i 's/__;Iw!!A4F2R9G_pg!M_S.*>/,/g' kb_discrepancy.txt
```


### Match semantic version at the beginning of the line and append the next line

```bash
awk '/^[0-9]+\.[0-9].*/ {l = $0; getline; printf "%s", l} 1' file.txt
```

### Append pattern line with a comma

```bash
awk '/^[0-9]+\.[0-9].*/ {$0=$0","} 1' file.txt
```

### Get Hub cert

```bash
echo | openssl s_client -servername $HUB_URL -connect $HUB_URL:443 | sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' > certificate.crt
```

### Get the list of .bdio files on the Hub instance
```bash
curl "$HUB"'/api/codelocations' -H 'Cookie: AUTHORIZATION_BEARER='"$AUTH_BEARER" | jq | egrep "\"name\"|bdio"
```
