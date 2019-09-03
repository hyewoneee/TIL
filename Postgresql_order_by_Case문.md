Postgresql 9.5이하거나 다른 DB를 사용할 경우 order by에 Case문을 사용할 수 있다.

	ORDER BY
	  CASE WHEN(
	    insert_timestamp > '2012-09-05 16:05:41.870117')
	  THEN 0
  	WHEN(insert_timestamp > '2012-09-04 16:05:41.870117')
	  THEN 2
	  WHEN(insert_timestamp > '2012-09-04 16:05:41.870117')
	  THEN 3
	  ELSE 4
	  END

order by를 커스텀 할 수 있다.

- order by 기준을 list로 하고 싶을 때

	order_by(Case(*[When(feed_no=no, then=index) for index, no in enumerate(feed_list[0])]))


