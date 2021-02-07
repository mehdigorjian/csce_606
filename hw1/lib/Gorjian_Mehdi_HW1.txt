# When done, submit this entire file to the autograder.

# Part 1

def sum arr
  arr.inject(0, :+)
end

def max_2_sum arr
  sum(arr.sort.last(2))
end

def sum_to_n? arr, n
  # arr.product(arr).any? {|couple| sum(couple) == n}
  return false if arr.empty? or arr.length == 1
	h = Hash.new
	arr.each{|x| 
		if h.key? x
			return true
		else
			h[n - x] = n	
		end
	}
	return false
end

# Part 2

def hello(name)
  %Q(Hello, #{name})
end

def starts_with_consonant? s
  /^[b-df-hj-np-tv-z]/i.match(s) != nil
end

def binary_multiple_of_4? s
  return true if s == "0"
	/^[10]*00$/.match(s) != nil
end

# Part 3

class BookInStock
  attr_accessor :isbn
	attr_accessor :price

	def initialize(isbn, price)
		raise ArgumentError, 
			"Illegal argument" if isbn.empty?  or price <= 0
		@isbn = isbn
		@price = price
	end

	def price_as_string
		sprintf("$%2.2f", @price)
	end
end
