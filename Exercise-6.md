6) Create a procedure called spSummariseEpisodes to show:

the 3 most frequently-appearing companions; then separately
the 3 most frequently-appearing enemies.

<pre>
  Solution 1:
  -- ================================================
  -- ================================================
  SET ANSI_NULLS ON
  GO
  SET QUOTED_IDENTIFIER ON
  GO
  -- =============================================
  -- Author:		Moumita Sen.
  -- Create date: 19/02/2022.
  -- Description:	This exercise will find the top 3 companions and enemies based on their frequencies.
  -- =============================================
  CREATE PROCEDURE sp_SummariseEpisodes 
  AS
  BEGIN
    -- SET NOCOUNT ON added to prevent extra result sets from
    -- interfering with SELECT statements.
    SET NOCOUNT ON;
    SELECT 
    DISTINCT TOP 3 (comp.CompanionName),
    COUNT(epiComp.CompanionId) OVER (PARTITION BY epiComp.CompanionId) AS OccurenceNumber
    FROM tblEpisodeCompanion epiComp
    INNER JOIN tblCompanion comp
    ON comp.CompanionId = epiComp.CompanionId
    ORDER BY OccurenceNumber DESC;

    SELECT 
    DISTINCT TOP 3 (ene.EnemyName),
    COUNT(epiEne.EnemyId) OVER (PARTITION BY epiEne.EnemyId) AS OccurenceNumber
    FROM tblEpisodeEnemy epiEne
    INNER JOIN tblEnemy ene
    ON ene.EnemyId = epiEne.EnemyId
    ORDER BY OccurenceNumber DESC;

  END
  GO

</pre>
<br>
<pre>
  Solution 2:
  -- ================================================
  -- ================================================
  SET ANSI_NULLS ON
  GO
  SET QUOTED_IDENTIFIER ON
  GO
  -- =============================================
  -- Author:		Moumita Sen.
  -- Create date: 19/02/2022.
  -- Description:	This exercise will find the top 3 companions and enemies based on their frequencies.
  -- =============================================
  CREATE PROCEDURE sp_SummariseEpisodes 
  AS
  BEGIN
    -- SET NOCOUNT ON added to prevent extra result sets from
    -- interfering with SELECT statements.
    SET NOCOUNT ON;

    SELECT TOP 3 comp.CompanionName, SUBTABLE.countComp Episodes
    FROM tblCompanion comp
    INNER JOIN (
      SELECT CompanionId, COUNT(epiComp.CompanionId) countComp
      FROM tblEpisodeCompanion epiComp
      GROUP BY CompanionId
    ) SUBTABLE
    ON comp.CompanionId = SUBTABLE.CompanionId
    ORDER BY CountComp DESC;

    SELECT TOP 3 ene.EnemyName, SUBTABLE.countEne Episodes
    FROM tblEnemy ene
    INNER JOIN (
      SELECT EnemyId, COUNT(epiEne.EnemyId) countEne
      FROM tblEpisodeEnemy epiEne
      GROUP BY epiEne.EnemyId
    ) SUBTABLE
    ON ene.EnemyId = SUBTABLE.EnemyId
    ORDER BY countEne DESC;

  END
  GO

  
</pre>
