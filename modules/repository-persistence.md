# Repository Persistence Layer
M2 S4 STORE/PRUNE/RETRIEVE file I/O implementation.

## Storage
~/.qclaw/se-experiences/
├── patterns/[task_type]/[id].json
├── rules/[task_type]/[id].json
├── transfers/[id].json
├── problems/open.json
├── problems/resolved.json
└── meta/index.json

## Entry Schema
```
{"id":"","type":"pattern|rule|transfer","task_type":"","domain":"","description":"","content":{"factors":[],"model":"","principle":"","confidence":0.0},"meta":{"version":1,"superseded_by":null,"conflict_with":null,"created":"ISO","last_updated":"ISO","source_session":""}}
```

## STORE
Write JSON → update index.json | duplicate: confidence+0.1|max1.0 | conflict: flag both conflict_resolution.pending

## RETRIEVE
Read index→filter(task_type)→top-3×(confidence×recency) | recency=1-min((now-last)/(30×86400),1) | empty→"REPO:no matching"

## PRUNE
30d+conf<0.5→archive | total>100→delete lowest | conflicts never deleted

## INIT
mkdir -p ~/.qclaw/se-experiences/{patterns,rules,transfers,problems,meta}
Write index.json/open.json