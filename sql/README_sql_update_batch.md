# 批量更新一条记录中的单个字段
UPDATE user
    SET name = CASE id
        WHEN 1 THEN 'update_name1'
        WHEN 2 THEN 'update_name2'
    END
WHERE id IN (1, 2);

# 批量更新一条记录中的多个字段
UPDATE user
    SET name = CASE id
        WHEN 3 THEN 'update_name3'
        WHEN 4 THEN 'update_name4'
    END,
    pwd = CASE id
        WHEN 5 THEN 'update_pwd5'
    END
WHERE id IN (3, 4, 5);

# 批量更新数据

    UPDATE test.t_table tr
    SET road = t.road,
        mesh = t.mesh,
        s_lanes = t.s_lanes,
        is_all = t.is_all
    FROM (SELECT 12345678 AS road,
                'H12345678' AS mesh,
                2 AS s_lanes,
                'N' AS is_all) AS t
    WHERE tr.road = t.road
    AND   tr.mesh = t.mesh;