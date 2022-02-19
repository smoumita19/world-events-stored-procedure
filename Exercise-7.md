7) Create a query which shows the 5 least-frequently appearing companions, and 5 least-frequently appearing enemies.
<pre>
  Solution:
  -- ================================================
  -- ================================================
  SET ANSI_NULLS ON
  GO
  SET QUOTED_IDENTIFIER ON
  GO
  -- =============================================
  -- Author:		Moumita Sen
  -- Create date: 19/02/2022
  -- Description:	Top three enemies who least appeared in the episode
  -- =============================================
  CREATE PROCEDURE spSummeriseEne

  AS
  BEGIN
    -- SET NOCOUNT ON added to prevent extra result sets from
    -- interfering with SELECT statements
    SET NOCOUNT ON;
    SELECT TOP 3 ENE.EnemyName, SUBTABLE.countEne
    FROM tblEnemy ENE
    INNER JOIN (
      SELECT epiEne.EnemyId, COUNT(epiEne.EnemyId) countEne
      FROM tblEpisodeEnemy epiEne
      GROUP BY epiEne.EnemyId 
    ) SUBTABLE
    ON ENE.EnemyId = SUBTABLE.EnemyId
    ORDER BY SUBTABLE.countEne
  END
  GO

</pre>

