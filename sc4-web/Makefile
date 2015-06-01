# Makefile for building a completely self-contained version of SC4 that
# can be run from a file: URL

TARGET=sc4z.html

OFFSET=$(shell grep -n 'SC4 HTML starts here' sc4.html | cut -f1 -d: )

${TARGET}: jquery.js nacl.js purify.js sc4.js sc4.css sc4.html
	echo '<meta charset="UTF-8">' >> $(TARGET)
	echo '<!-- This is a self-contained version of SC4 -->' > $(TARGET)
	echo '<!-- See https://sc4.us/ for more information -->' >> $(TARGET)
	echo '<style>' >> ${TARGET}
	cat sc4.css >> ${TARGET}
	echo '</style>' >> ${TARGET}
	echo '<script>' >> ${TARGET}
	cat jquery.js purify.js nacl.js sc4.js >> ${TARGET}
	echo 'sc4.genlocal_flag = true;' >> ${TARGET}
	echo '</script>' >> ${TARGET}
	tail -n +${OFFSET} sc4.html >> ${TARGET}

clean:
	rm $(TARGET)
