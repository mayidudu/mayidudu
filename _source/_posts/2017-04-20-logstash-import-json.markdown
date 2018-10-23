
```
input {
        file {
                type => "zmap"
                path => ["/home/hadoop/rawdoc/ipv4json/*"]
                codec => "json"
                start_position => "beginning"
                sincedb_path => "/dev/null"
        }
}
output {
        elasticsearch {
                hosts => ["localhost:9200"]
                index => "test3"
                codec => json
                template_overwrite => true
        }

}
```