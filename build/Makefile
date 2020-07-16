# target to make the file report
all: 05_final_report.html

googlebooks-eng-all-1gram-20120701-1.gz: # add filenames for data and/or code this output depends on here
	# add code to run script to download the 1grams data here
	url=http://storage.googleapis.com/books/ngrams/books/googlebooks-eng-all-1gram-20120701-1.gz
	[ -f googlebooks-eng-all-1gram-20120701-1.gz ] || curl -o googlebooks-eng-all-1gram-20120701-1.gz $url
	touch googlebooks-eng-all-1gram-20120701-1.gz

year_counts.tsv: # add filenames for data and/or code this output depends on here 
	# add code to run script to filter the 1grams data here
	zless googlebooks-eng-all-1gram-20120701-1.gz | grep -E '^(18|19|20)[0-9][0-9][[:space:]]' >> year_counts.tsv

googlebooks-eng-all-totalcounts-20120701.txt: # add filenames for data and/or code this output depends on here
	# add code to run script to download the total counts data here
	url=http://storage.googleapis.com/books/ngrams/books/googlebooks-eng-all-totalcounts-20120701.txt
	[ -f googlebooks-eng-all-totalcounts-20120701.txt ] || curl -o googlebooks-eng-all-totalcounts-20120701.txt $url
	touch googlebooks-eng-all-totalcounts-20120701.txt

total_counts.csv: # add filenames for data and/or code this output depends on here
	# add code to run script to reformat the total counts data here
	cat googlebooks-eng-all-totalcounts-20120701.txt | tr "\t" "\n" >> total_counts.csv 

05_final_report.html: # add filenames for data and/or code this output depends on here
	Rscript -e "rmarkdown::render('05_final_report.Rmd')"
