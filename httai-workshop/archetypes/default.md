---
title: "{{ $dir := replace .File.Dir "\\" "/" }}{{ $folder := last 1 (split (trim $dir "/") "/") }}{{ $name := index $folder 0 }}{{ replace (replaceRE `^[0-9]+(\.[0-9]+)*[-_]?` "" $name) "-" " " | title }}"
date: "{{ (time .Date).Format "2006-01-02" }}"
weight: {{ $dir := replace .File.Dir "\\" "/" }}{{ $folder := last 1 (split (trim $dir "/") "/") }}{{ $name := index $folder 0 }}{{ with findRE `[0-9]+$` $name }}{{ index . 0 }}{{ else }}{{ with findRE `^[0-9]+(\.[0-9]+)*` $name }}{{ $parts := split (index . 0) "." }}{{ if gt (len $parts) 1 }}{{ index $parts 1 }}{{ else }}{{ index $parts 0 }}{{ end }}{{ else }}1{{ end }}{{ end }}
chapter: false
pre: " <b> {{ $dir := replace .File.Dir "\\" "/" }}{{ $folder := last 1 (split (trim $dir "/") "/") }}{{ $name := index $folder 0 }}{{ with findRE `^[0-9]+(\.[0-9]+)*` $name }}{{ index . 0 }}.{{ else }}1.{{ end }} </b> "
---