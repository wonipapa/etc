SELECT
distinct librairy.name as category,
serie.title as name
FROM
metadata_items episode JOIN metadata_items season ON season.id = episode.parent_id JOIN metadata_items serie ON serie.id = season.parent_id
JOIN library_sections librairy ON librairy.id = episode.library_section_id
WHERE
DATE(episode.added_at)  >= (SELECT DATE('now', '-1 day'))
ORDER BY
category
