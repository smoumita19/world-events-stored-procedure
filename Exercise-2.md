2) Write a SELECT statement in SQL to list out all of the episodes which featured Matt Smith as the Doctor.
<pre>
  -- ================================================
  -- ================================================
  SET ANSI_NULLS ON
  GO
  SET QUOTED_IDENTIFIER ON
  GO
  -- =============================================
  -- Author:		Moumita Sen
  -- Create date: 18/02/2022
  -- Description:	This 
  -- =============================================
  CREATE PROCEDURE sp_Episodes 
  AS
    -- SET NOCOUNT ON added to prevent extra result sets from
    -- interfering with SELECT statements.
    SET NOCOUNT ON;

    SELECT epi.[SeriesNumber] AS Series, epi.[EpisodeNumber] Episode, epi.[Title] TITLE, 
    epi.[EpisodeDate] 'DATE OF EPISODE', 
    doc.[DoctorName] DOCTOR,
    aut.[AuthorName] Author
    FROM [dbo].[tblEpisode] epi
    INNER JOIN [dbo].[tblDoctor] doc ON epi.[DoctorId] = doc.[DoctorId] 
    INNER JOIN [dbo].[tblAuthor] aut ON epi.[AuthorId] = aut.[AuthorId]
    AND doc.[DoctorName] = 'Matt Smith'
    ORDER BY epi.[EpisodeDate];
  GO
</pre>


