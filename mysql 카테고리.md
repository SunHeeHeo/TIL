//카테고리 포함 전체 조회
router.get('/category', function (req, res, next) {
  let conditions = [];
  let where
  console.log("get method 연결완료!")
  const {dogSize, dogGender, dogAge, locationCategory, completed} = req.body;
  console.log(dogSize, dogGender, dogAge, locationCategory, completed)

  //카테고리 필터 
  if(dogSize !== 'undefined'){
    conditions.push(`dogSize = '${dogSize}'`);
  }
  if(dogGender !== 'undefined'){
    conditions.push(`dogGender = '${dogGender}'`);
  }
  if(dogAge !== 'undefined'){
    conditions.push(`dogAge = '${dogAge}'`);
  }
  if(locationCategory !== 'undefined'){
    conditions.push(`locationCategory = '${locationCategory}'`);
  }
  if(completed !== 'undefined'){
    conditions.push(`completed = '${completed}'`);
  }
  where = conditions.join(' AND ' );
  console.log('where', where);

  try {
    console.log(4)
    const query = `SELECT dog.dogId, dog.dogGender, dog.dogName, dog.dogSize, dog.dogBreed, dog.dogAge, dog.neutral, dog.dogComment, dog.dogImage, dog.userId,
    post.userId, post.postId, post.meetingDate, post.completed, post.locationCategory  
    FROM post
    JOIN dog
    ON dog.userId=post.userId
    WHERE ` + where 
    console.log('query', typeof query);
    db.query(query, (error, rows) => {
      console.log('6');
      if (error) {
        console.log(error)
        // logger.error('게시글 조회 중 발생한 DB관련 에러', error);
        return res.sendStatus(400);
      }
      console.log('7');
      // logger.info('게시글을 성공적으로 조회했습니다.');
      res.status(200).json({
        success: true,
        posts: rows,
      });
      console.log("rows는", rows)
    });

  } catch (err) {
    // logger.error('게시글 조회하기 중 발생한 예상하지 못한 에러: ', err);
    return res.sendStatus(500);
  }
});


